## 웹 프로그래밍 기말과제 「나의 취미 페이지 만들기」

 2021학년도 1학기 웹프로그래밍 기말과제 프로젝트. 

​	자신의 관심사나 취미를 주제로 페이지를 만드는 것 이었습니다. 1학년을 마치고 C, Python 이외에 다른 언어를 공부해보고 싶었고 메이커스페이스에서 일을 하며 3D 프린터 사용대장을 웹페이지로 만들고자 HTML 태그와 CSS보다는 JavaScript나 jqeury를 위주로 독학하였습니다. 이번 웹프로그래밍 강의를 듣고 HTML태그들과 여러가지 CSS 속성들을 배우며 복잡했던 머릿속을 하나하나 정리해갈 수 있었던 강의였습니다.

[완성 사이트] : https://sungjaesportfolio.netlify.app/

### 개요

​	저의 관심사나 취미는 노래, 노래부르기 입니다. 뭐 배드민턴이나 영화보기 이런것들도 있습니다. ㅎㅎ 처음에는 영화를 주제로 여러 영화를 소개하는 페이지를 만들려고 했지만 노래를 주제로 선택하였습니다. 다음에 영화를 주제로 만들어보는것도 재미있을 것 같네요^^

​	수업시간에 여러가지 CSS 속성 수업 PPT를 보고 영감을 얻어 홈화면을 디자인 하게되었습니다. 왼쪽 사진은 수업시간에 나왔던 PPT이고 오른쪽 사진은 이번 프로젝트로 만든 페이지 디자인 입니다.

<img src="사진\기말 프로젝트 영감.png" alt="기말 프로젝트 영감" style="zoom:50%; float: left;" /><img src="사진\기말 프로젝트 화면 구성.png" alt="기말 프로젝트 화면 구성" style="zoom:16%;" />



### 페이지 기능 및 코드 설명

​	**1.  페이지 기능**

1. 페이지 디자인 아이디어 기본 코드

```html
<style>
    .Music{
            margin: 0 auto;
            position: relative;
            width: 50%;
            height: 70%;
            top: 100px;
        }
        .Music_1{
            position: absolute;
            background-color: red;
            width: 60%;
            height: 400px;  
            transition: all .5s;		/* 요소 안에 있는 모든 변화를 부드럽게 */
        }
        .Music_1:hover{
            transform: translate(20% , -9%);
        }
        .Music_2{
            position: absolute;
            background-color: yellow;
            width: 60%;
            height: 400px;
            right: 250px;
            top: 50px;
            z-index: 1;
            transition: all .5s;
        }
        .Music_2:hover{
            transform: translate(20% , -9%);
        }
</style>

<div class="Music">
    <div class="Music_1" id="Music_1">
    	<!-- 안에 들어갈 내용 -->
    </div>
    <div class="Music_2" id="Music_2">
    	<!-- 안에 들어갈 내용 -->
    </div>
</div>
```

![페이지 아이디어 영상](https://user-images.githubusercontent.com/88194064/131795312-eb7fbc32-ecde-46d3-8af6-444eec72b277.gif)

영상 두번째 컷은 transition O

2. 마우스오버시 노래 재생

```html
<h1 onmouseover="hzplay('Standing EGG - Little Star.mp3')" onmouseleave="hzplay('')">Littel Star</h1>
<audio id='hz' controls><source src="" type="audio/mp3" /></audio>
```

```javascript
function hzplay($mp3){
    hz = document.getElementById("hz");
    hz.src = $mp3;
    hz.play();				//노래 재생
    hz.volume = 0.08;		//노래 볼륨
}
```

![페이지 오디오 아이디어 영상](https://user-images.githubusercontent.com/88194064/131795363-d7b594ee-71ea-4206-be3c-6b1a22b4128f.gif)

3. 로그인

```html
<div class="Content">
    <div class="content">
        <h1>아이디</h1>
        <form id="idform">
            <input type="id" name="id" id="UserId" placeholder="아이디를 입력해주세요...">
        </form>
        <h1>패스워드</h1>
        <form id="passform">
            <input type="password" name="pass" id="password" placeholder="비밀번호를 입력해주			세요...">
        </form>
        <br>
        <br>
        <button id="submit">로그인</button>
    </div>
</div>
```

```javascript
document.getElementById('submit').onclick = function() {
    var ID = document.getElementById('UserId').value;
    var pass = document.getElementById('password').value;
    if (ID === "1111" && pass === "1234") {
        alert("안녕하세요!");
        location.href="../home/home.html";
    }
    else if(ID === "1111"){					 //비밀번호 오류
        alert("비밀번호를 다시 확인하세요.");
    }
    else if(pass === "1234"){				 //아이디 오류
        alert("아이디를 다시 확인하세요.");
    }
    else if(ID != "1111" && pass != "1234"){ //아이디, 비밀번호 오류
        alert("아이디와 비밀번호를 다시 확인하세요.");
    }
}
```

4. 달력(현재 시간)

```html
<div class="Calendar">
        <div class = "Title">
            <h1>5월 일정 시간표</h1>
        </div>
        <div class = "calendar">
            <table>
                <thead>
                    <tr>
                        <th>일</th>
                        <th>월</th>
                        <th>화</th>
                        <th>수</th>
                        <th>목</th>
                        <th>금</th>
                        <th>토</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td class="Last_month">25</td>
                        <td class="Last_month">26</td>
                        <td class="Last_month">27</td>
                        <td class="Last_month">28</td>
                        <td class="Last_month">29</td>
                        <td class="Last_month">30</td>
                        <td id="1">1</td>
                    </tr>
                    <tr>
                        <td id="2">2</td>
                        <td id="3">3</td>
                        <td id="4">4</td>
                        <td id="5">5</td>
                        <td id="6" class="Work">6<p>Camp51.9 출근<br>시간 : 17:00 ~ 21:00</p></td>
                        <td id="7" class="Work">7<p>Camp51.9 출근<br>시간 : 16:00 ~ 20:00</p></td>
                        <td id="8" class="Work">8<p>Camp51.9 출근<br>시간 : 9:00 ~ 15:00</p></td>
                    </tr>
                    <tr>
                        <td id="9">9</td>
                        <td id="10">10</td>
                        <td id="11" class="Work" style="background-color: rgb(57, 143, 255);">11<p>신호및시스템 중간고사 <br>시간: 10:30 ~ 11:00</p></td>
```

```html
                        <td id="12" class="Work">12<p>Camp51.9 출근<br>시간 : 16:00 ~ 20:00</p></td>
                        <td id="13" class="Work">13<p>Camp51.9 출근<br>시간 : 16:00 ~ 21:00</p></td>
                        <td id="14" class="Work">14<p>Camp51.9 출근<br>시간 : 16:00 ~ 21:00</p></td>
                        <td id="15">15</td>
                    </tr>
                    <tr>
                        <td id="16">16</td>
                        <td id="17">17</td>
                        <td id="18">18</td>
                        <td id="19">19</td>
                        <td id="20" class="Work">20<p>Camp51.9 출근<br>시간 : 17:00 ~ 21:00</p></td>
                        <td id="21" class="Work">21<p>Camp51.9 출근<br>시간 : 16:00 ~ 20:00</p></td>
                        <td id="22" class="Work">22<p>Camp51.9 출근<br>시간 : 9:00 ~ 15:00</p></td>
                    </tr>
                    <tr>
                        <td id="23">23</td>
                        <td id="24">24</td>
                        <td id="25">25</td>
                        <td id="26" class="Work">26<p>Camp51.9 출근<br>시간 : 16:00 ~ 20:00</p></td>
                        <td id="27" class="Work">27<p>Camp51.9 출근<br>시간 : 16:00 ~ 21:00</p></td>
                        <td id="28" class="Work">28<p>Camp51.9 출근<br>시간 : 16:00 ~ 21:00</p></td>
                        <td id="29">29</td>
                    </tr>
                    <tr>
                        <td id="30">30</td>
                        <td id="3">31</td>
                        <td class = "Next_month">1</td>
                        <td class = "Next_month">2</td>
                        <td class = "Next_month">3</td>
                        <td class = "Next_month">4</td>
                        <td class = "Next_month">5</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
```

```javascript
if(month0 == 5){
    $(document).ready(function() {
        $("#Calendar").html('5월 달력 HTML 데이터')
    })
}
if(month0 == 6){
    $(document).ready(function() {
        $("#Calendar").html('6월 달력 HTML 데이터')
    })
}
```

```javascript
$(document).ready(function(){
    $('#' + date).addClass("today")
})
```



### 느낀점

 웹프로그래밍 강의를 듣고 혼자 구글 검색을 통해 HTML을공부하며 복잡했던 머릿속을 하나하나 정리할 수 있어서 좋았다. 나의 취미 노래를 주제로 페이지를 디자인하였는데, 수업시간에 배운 내용을 사용하여 머릿속에 상상한 디자인 그대로 페이지를 디자인 할 수 있었다. 페이지의 기본적인 틀을 생각하고 그 틀에 맞춰 만들어 갔는데 무작정 만드는 것 보다 더 빠르고 편했다. 그래서 더욱 이번 프로젝트가 재미있었고 HTML 또는 다른 코딩 언어를 배우는 것에 자신감이 붙는 계기가 되었던 것 같다. 
