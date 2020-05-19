<html>
<head>
<title>Random Orica Generator v1.0</title>
</head>
<body>

	<h1>Random Orica Generator</h1>

	<textarea cols="50" rows="35" id='card'>ORICA!</textarea>

<script type="text/javascript">
	
	////Variables
	var rac = ["전사족","마법사족","천사족","악마족","언데드족",
			"기계족","물족","화염족","암석족","비행야수족","식물족",
			"곤충족","번개족","드래곤족","야수족","야수전사족","공룡족",
			"어류족","해룡족","파충류족","사이킥족","환신야수족","창조신족",
			"환룡족","사이버스족"];
	var att = ["地","水","炎", "風", "光", "闇", "神"];
	var cat = ["융합","싱크로","엑시즈","링크","의식",
			"효과","효과","효과","효과","효과",
			"마법","마법","마법","함정","함정"];
	var ico = ["속공","장착","필드","일반","지속","카운터"];
	var eff = ["마법/함정 파괴","몬스터 파괴","제외","묘지로",
			"패 바운스","덱 바운스","패 파괴","덱 파괴","드로우",
			"서치","회수","표시 형식","컨트롤","공수 변경","관통",
			"연속 공격","공격 제한","직접 공격","특수 소환","토큰",
			"종족","속성","LP 데미지","LP 회복","파괴 내성","효과 내성",
			"카운터","겜블","융합","싱크로","엑시즈","효과 무효"];
	var loc = ["몬스터 존","엑스트라 몬스터 존","패","묘지","제외 존","마법 & 함정 존"];
	var scl = ["턴제 없음","턴제 없음","1턴 1번","1턴 1번","명칭 1턴 1번","명칭 1턴 1번","듀얼 1턴 1번"];
	var lnk = ["→","←","↑","↓","↗","↙","↖","↘"];

	var cardType, cardloc, star, atk, def, icon, starS, asset, effect;
	////

	cardType = dRes(cat);
	effect = "";
	if(cardType < 10){
		asset = rac[dRes(rac)] + "\n" + att[dRes(att)] + "\n" + cat[cardType] + "\n";
		starS = "★";
		star = rD(12);
		atk = (star*3)+rD(4)+rD(4);
		def = [(star*2)+rD(6)+rD(6)+rD(6)]*100;
		if (cardType == 3) {
			starS = "L"
			star = rD(4);
			atk += (4*star)-2;
			def = "";
			for (i = 0; i < star; i++) {
				while (true) {
					icon=lnk[dRes(lnk)];
					if (def.indexOf(icon)<0) {
						def+=icon;
						break;
					}
				}
			}
		}
		asset += starS + star + "\n" + (atk*100) + " / " + def + "\n";
	}
	else{
		while (true){
			icon=rD(6);
			if (cardType>12 && icon>3) break;
			else if (cardType<13 && icon!=6) break;
		}
		asset = cat[cardType] + "\n" + ico[icon-1] + "\n";
	}

	for(i = 0; i < rD(3); i++) {
		cardloc=1;
		while (true){
			if (cardType<9){
				cardloc=rD(5);
				if (cardType<4 && cardloc!=3) break;
				else if (cardType>3 && cardloc!=2) break;
			}
			else{
				cardloc=rD(3)+3;
				break;
			}
		}
		if (cardType>9 && i==0) cardloc=6;
		effect += ("\n효과 " + (i+1) + " =====\n" + eff[dRes(eff)] + "\n" + loc[cardloc-1] + "\n" + scl[dRes(scl)] + "\n")
	}
	
	var finalText = document.getElementById('card');
	finalText.value = (asset + effect);

	function rD(m) {
		return Math.floor(Math.random()*(m))+1;
	}
	function dRes(a){
		return [rD(a.length)-1];
	}
		
    </script>
</body>
</html>
