# 스프링을 이용해서 다음과 같은 환율계산 웹 기능을 만듭니다.
첫화면은 다음과 같습니다.  

<kbd>
 <img src="https://github.com/wirebarley/apply/blob/master/images/coding_test1.png">
</kbd>

- 송금국가는 미국으로 고정입니다. 통화는 미국달러(USD)입니다. 
- 수취국가는 한국, 일본, 필리핀 세 군데 중 하나를 select box로 선택합니다. 각각 통화는 KRW, JPY, PHP 입니다.
- 수취국가를 선택하면 아래 환율이 바뀌어나타나야 합니다. 환율은 1 USD 기준으로 각각 KRW, JPY, PHP의 대응 금액입니다.
- 송금액을 USD로 입력하고 Submit을 누르면 아래 다음과 같이 수취금액이 KRW, JPY, PHP 중 하나로 계산되어서 나와야 합니다.
- 환율과 수취금액은 소숫점 2째자리까지, 3자리 이상 되면 콤마를 가운데 찍어 보여줍니다. 예를 들어 1234라면 1,234.00으로 나타냅니다.

<kbd>
 <img src="https://github.com/wirebarley/apply/blob/master/images/coding_test3.png">
</kbd>

- 환율정보는 https://currencylayer.com/ 의 무료 서비스를 이용해서 실시간으로 가져와야 합니다. 웹 서버가 시작될 때 한번 가져와서 계속 사용해도 되고, 매번 새로운 환율 정보를 가져와도 됩니다. 
- 새로운 무료 계정을 등록해서 API 키를 받아서 사용하면 됩니다. 샘플로 등록된 계정의 키를 예를 들면 다음과 같습니다.
<http://www.apilayer.net/api/live?access_key=ee50cd7cc73c9b7a7bb3d9617cfb6b9c>

결과로 다음과 같이 JSON으로 된 환율정보를 돌려받습니다.

```json
{  
    "success":true,
    "terms":"https:\/\/currencylayer.com\/terms",
    "privacy":"https:\/\/currencylayer.com\/privacy",
    "timestamp":1545881647,
    "source":"USD",
    "quotes":{  
        "USDAED":3.673197,
        "USDAFN":76.088502,
        "USDALL":108.014949,
        "USDAMD":484.684999,
        "USDANG":1.78935,
        "USDAOA":308.428019,
        "USDARS":38.025498,
        "USDAUD":1.41645,
        "USDAWG":1.8005,
        "USDAZN":1.704992,
        "USDBAM":1.720195,
        "USDBBD":2.0065,
        "USDBDT":84.095497,
        "USDBGN":1.720202,
        "USDBHD":0.377845,
        "USDBIF":1796.55,
        "USDBMD":1,
        "USDBND":1.375902,
        "USDBOB":6.926599,
        "USDBRL":3.921797,
        "USDBSD":1.002425,
        "USDBTC":0.000264,
        "USDBTN":70.202655,
        "USDBWP":10.813986,
        "USDBYN":2.143987,
        "USDBYR":19600,
        "USDBZD":2.02065,
        "USDCAD":1.359085,
        "USDCDF":1631.000242,
        "USDCHF":0.992601,
        "USDCLF":0.025048,
        "USDCLP":693.601955,
        "USDCNY":6.891597,
        "USDCOP":3302.1,
        "USDCRC":600.159866,
        "USDCUC":1,
        "USDCUP":26.5,
        "USDCVE":96.98802,
        "USDCZK":22.743597,
        "USDDJF":177.720369,
        "USDDKK":6.55895,
        "USDDOP":50.863502,
        "USDDZD":118.89004,
        "USDEGP":17.935975,
        "USDERN":15.000356,
        "USDETB":28.186971,
        "USDEUR":0.878695,
        "USDFJD":2.134978,
        "USDFKP":0.790015,
        "USDGBP":0.790055,
        "USDGEL":2.664971,
        "USDGGP":0.790081,
        "USDGHS":4.92205,
        "USDGIP":0.790015,
        "USDGMD":49.349825,
        "USDGNF":9119.750355,
        "USDGTQ":7.753973,
        "USDGYD":209.405028,
        "USDHKD":7.83205,
        "USDHNL":24.452983,
        "USDHRK":6.528297,
        "USDHTG":77.535503,
        "USDHUF":282.139656,
        "USDIDR":14562.5,
        "USDILS":3.77795,
        "USDIMP":0.790081,
        "USDINR":70.255029,
        "USDIQD":1196.15,
        "USDIRR":42105.000352,
        "USDISK":117.039989,
        "USDJEP":0.790081,
        "USDJMD":128.584974,
        "USDJOD":0.71021,
        "USDJPY":110.959498,
        "USDKES":102.009392,
        "USDKGS":69.850079,
        "USDKHR":4034.850439,
        "USDKMF":433.624965,
        "USDKPW":900.056691,
        "USDKRW":1121.419945,
        "USDKWD":0.30395,
        "USDKYD":0.835385,
        "USDKZT":371.980321,
        "USDLAK":8577.350421,
        "USDLBP":1511.700215,
        "USDLKR":181.995016,
        "USDLRD":157.49779,
        "USDLSL":14.580079,
        "USDLTL":2.95274,
        "USDLVL":0.60489,
        "USDLYD":1.398302,
        "USDMAD":9.57215,
        "USDMDL":17.241499,
        "USDMGA":3546.103567,
        "USDMKD":54.068501,
        "USDMMK":1570.350024,
        "USDMNT":2637.254916,
        "USDMOP":8.087899,
        "USDMRO":356.999895,
        "USDMUR":34.397439,
        "USDMVR":15.449742,
        "USDMWK":730.9697,
        "USDMXN":19.894202,
        "USDMYR":4.176501,
        "USDMZN":61.490214,
        "USDNAD":14.579558,
        "USDNGN":365.14006,
        "USDNIO":32.539886,
        "USDNOK":8.74611,
        "USDNPR":112.505037,
        "USDNZD":1.48712,
        "USDOMR":0.38613,
        "USDPAB":1.002415,
        "USDPEN":3.3677,
        "USDPGK":3.37735,
        "USDPHP":52.72027,
        "USDPKR":140.215019,
        "USDPLN":3.76165,
        "USDPYG":5935.90292,
        "USDQAR":3.641105,
        "USDRON":4.073703,
        "USDRSD":103.902084,
        "USDRUB":68.953405,
        "USDRWF":895.105,
        "USDSAR":3.760902,
        "USDSBD":8.20555,
        "USDSCR":13.683499,
        "USDSDG":47.736004,
        "USDSEK":9.066405,
        "USDSGD":1.37275,
        "USDSHP":1.320899,
        "USDSLL":8599.9997,
        "USDSOS":580.000195,
        "USDSRD":7.457965,
        "USDSTD":21050.59961,
        "USDSVC":8.770703,
        "USDSYP":514.999392,
        "USDSZL":14.583503,
        "USDTHB":32.607967,
        "USDTJS":9.44805,
        "USDTMT":3.5,
        "USDTND":3.00425,
        "USDTOP":2.25965,
        "USDTRY":5.277175,
        "USDTTD":6.794603,
        "USDTWD":30.796503,
        "USDTZS":2299.901063,
        "USDUAH":27.443502,
        "USDUGX":3716.096617,
        "USDUSD":1,
        "USDUYU":32.344501,
        "USDUZS":8350.549968,
        "USDVEF":9.987501,
        "USDVND":23336.2,
        "USDVUV":113.783789,
        "USDWST":2.626846,
        "USDXAF":576.94015,
        "USDXAG":0.06652,
        "USDXAU":0.000787,
        "USDXCD":2.70255,
        "USDXDR":0.721204,
        "USDXOF":576.940096,
        "USDXPF":104.903214,
        "USDYER":250.349931,
        "USDZAR":14.523899,
        "USDZMK":9001.202279,
        "USDZMW":11.953972,
        "USDZWL":322.355011
    }
}
// JSON quotes 목록의 USDKRW이 KRW/USD 환율, USD/JPY이 JPY/USD 환율, USD/PHP가 PHP/USD 환율입니다. 이 환율 정보를 이용해서 환율 계산을 하면 됩니다.
```


- 환율을 미리 계산해서 html/javascript 안에 넣어두고 수취국가를 변경할 때마다 이를 자바스크립트로 바로 가져와서 보여줘도 좋고,
- 혹은 매번 수취국가를 선택/변경할 때마다 API로 서버에 요청을 해서 환율정보를 가져오게 해도 좋습니다.
- Submit을 누르면 선택된 수취국가와 그 환율, 그리고 송금액을 가지고 수취금액을 계산해서 하단에 보여주면 됩니다.
API를 이용해서 서버에서 계산해서 뿌려도 되고
자바스크립트로 미리 가져온 환율을 계산해서 수취금액을 보여줘도 되고
Submit 버튼으로 폼을 submit해서 화면을 새로 그려도 됩니다.
- 수취금액을 입력하지 않거나, 0보다 작은 금액이거나 10,000 USD보다 큰 금액, 혹은 바른 숫자가 아니라면 “송금액이 바르지 않습니다"라는 에러 메시지를 보여줍니다. 메시지는 팝업, 혹은 하단에 빨간 글씨로 나타나면 됩니다.


1. 본 테스트는 지원자의 스프링 숙련도를 보기 위한 테스트이며 핵심 기능(외부 API 처리, 에러핸들링등)을 스프링으로 구현하셔야 합니다.
2. API 설계 및 구현능력을 중점적으로 봅니다.
3. 사용기술은 스프링 4.0이후 버전을 사용하면 어떤 기술을 이용해도 상관없습니다. 스프링 부트를 이용해도 됩니다.
4. 테스트 코드를 만드시면 가산점이 있습니다.
5. 클라이언트 화면은 스프링의 뷰 기술(jsp, thymeleaf 등)을 이용해도 좋고, React나 Angular 등을 이용해도 좋습니다.
6. 작성한 코드는 github에 올리고 조회가능한 주소를 보내주면 됩니다.
