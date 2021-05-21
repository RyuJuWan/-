# -
흩어져있는 소스들을 정리

highchart정리 (상세 그래프는 highchart demo검색...)
  1. 동적 데이터 추가
     
     1)그래프 선언
    
    const chart = Highcharts.chart('container', {
            chart: {
                events: {
                    addSeries: function () {
                        var label = this.renderer.label('A series was added, about to redraw chart', 100, 120)
                            .attr({
                                fill: Highcharts.getOptions().colors[0],
                                padding: 10,
                                r: 5,
                                zIndex: 8
                            })
                            .css({
                                color: '#FFFFFF'
                            })
                            .add();

                        setTimeout(function () {
                            label.fadeOut();
                        }, 1000);
                    }
                }
            },
            xAxis: {
                categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
            },
            series: [{
                data: [29.9, 71.5, 106.4, 129.2, 144.0, 176.0, 135.6, 148.5, 216.4, 194.1, 95.6, 54.4]
            }]
        });
     
   2) series 추가
    
          chart.addSeries({
              marker : {
                enabled : true,
                radius : 3
              },
              data: [216.4, 194.1, 95.6, 54.4, 29.9, 71.5, 106.4, 129.2, 144.0, 176.0, 135.6, 148.5]
          });
    
   3) addPoint
   
          chart.series[1].addPoint('juu',13);
        
        
        
 체크박스 버튼 만들기
 (드롭 체크 박스는 미존재)
 
    <div style="position:relative;z-index:1">
    <span id="searchOrnId" onClick="chiceSelectBox(this);"> 선택</span>
    <div id="testVal" class="testVal">
      <c:forEach var="item" items="${ornList}">
        <input type="checkbox" value="${item.ornId}" class="check" id="${item.ornId}" name="${item.ornNm}"/>${itme.ornNm}<br/>
      </c:forEach>
    </div>
    </div>


동적div에 스크롤 이벤트 추가 하기
※ onClick 이벤트 안에 scroll 액션을 넣어야 정상작동 된다!

HTML

     <input type="button" id="btn" value="Click"/>
     
JavaScript

      $(document).ready(function(){
          $("#btn").click(function(){
            if ($(".myDiv").length == 0) // Append once

          //1. 동적 div 생성
          $("body").append('<div class="myDiv"><br><br><p>Content1<p><br><br><p>Content2<p><br><br></div>');
        // 스크롤 액션 추가
        $(".myDiv").scroll(function(){
          alert("A1");
        });
        
CSS     

      .myDiv{
            height: 90px;
            width: 300px;
            border: 1px solid;
            background-color: lavender;
            overflow: auto;
        }

            





      });
