
### 연습문제 1번


```CSS
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ex1</title>
    <style>
       .list1 {
        border: 1px solid black;
        border-collapse: collapse;
        min-width: 100%;  /* 테이블이 최소한 100% 너비를 가지도록 설정 */
       }
       .list1-wrapper {
    width: 100%;
    overflow-x: auto;  /* 가로 스크롤 추가 */
}
       th,td {
        border: 1px solid black;
        text-align: center;
        padding: 2px 20px;
       }
       
       td.cell5 {
        text-align: left;
       }
       body {
           display: flex;
           justify-content: center;  
           align-items: center;      
           height: 100vh;            
           margin: 0;               
       }
       .main h2 {
           margin-bottom: 0;          /* h2 아래쪽 여백 제거 */
           padding-bottom: 0;         /* h2와 hr 사이의 여백 없애기 */
       }
       hr {
           margin-top: 0px;             /* hr 위쪽 여백 제거 */
           margin-bottom: 25px;          /* hr 아래쪽 여백 제거 */
       }
       th {
        background-color: grey;
       }
       h2::first-letter {
           color: red;  /* 첫 번째 글자만 빨간색으로 변경 */
           font-size: 1em;  /* 글자 크기도 커지도록 설정 가능 */
       }
       .table-design {
        font-weight: bold;
        font-size: 1.2em;
        text-align: right;
       }

    </style>
</head>
<body>
    <div class="main">
    <h2>Member List</h2>
    <span class="table-design">Table Design</span>
    <hr>
    <table class="list1">
        <thead>
            <tr>
                <th class="head1">No</th>
                <th class="head2">Name</th>
                <th class="head3">Age</th>
                <th class="head4">ID</th>
                <th class="head5">Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="cell1">01</td>
                <td class="cell2">Lorem</td>
                <td class="cell3">21</td>
                <td class="cell4">Lorem</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">02</td>
                <td class="cell2">Magni</td>
                <td class="cell3">22</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">03</td>
                <td class="cell2">Dolor</td>
                <td class="cell3">23</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">04</td>
                <td class="cell2">Sit</td>
                <td class="cell3">24</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">05</td>
                <td class="cell2">Amet</td>
                <td class="cell3">25</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">06</td>
                <td class="cell2">Facere</td>
                <td class="cell3">26</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">07</td>
                <td class="cell2">Voluptas</td>
                <td class="cell3">27</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">08</td>
                <td class="cell2">Consequuntur</td>
                <td class="cell3">28</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">09</td>
                <td class="cell2">Nesciunt</td>
                <td class="cell3">29</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">10</td>
                <td class="cell2">Dolorum</td>
                <td class="cell3">30</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
    
        </tbody>
    </table>
    <h2>Member List</h2>
    <span class="table-design">Table Design</span>
    <hr>
    <table class="list1">
        <thead>
            <tr>
                <th class="head1">No</th>
                <th class="head2">Name</th>
                <th class="head3">Age</th>
                <th class="head4">ID</th>
                <th class="head5">Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="cell1">01</td>
                <td class="cell2">Lorem</td>
                <td class="cell3">21</td>
                <td class="cell4">Lorem</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">02</td>
                <td class="cell2">Magni</td>
                <td class="cell3">22</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">03</td>
                <td class="cell2">Dolor</td>
                <td class="cell3">23</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">04</td>
                <td class="cell2">Sit</td>
                <td class="cell3">24</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">05</td>
                <td class="cell2">Amet</td>
                <td class="cell3">25</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">06</td>
                <td class="cell2">Facere</td>
                <td class="cell3">26</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">07</td>
                <td class="cell2">Voluptas</td>
                <td class="cell3">27</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">08</td>
                <td class="cell2">Consequuntur</td>
                <td class="cell3">28</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">09</td>
                <td class="cell2">Nesciunt</td>
                <td class="cell3">29</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">10</td>
                <td class="cell2">Dolorum</td>
                <td class="cell3">30</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
    
        </tbody>
    </table>
    <h2>Member List</h2>
    <span class="table-design">Table Design</span>
    <hr>
    <table class="list1">
        <thead>
            <tr>
                <th class="head1">No</th>
                <th class="head2">Name</th>
                <th class="head3">Age</th>
                <th class="head4">ID</th>
                <th class="head5">Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="cell1">01</td>
                <td class="cell2">Lorem</td>
                <td class="cell3">21</td>
                <td class="cell4">Lorem</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">02</td>
                <td class="cell2">Magni</td>
                <td class="cell3">22</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">03</td>
                <td class="cell2">Dolor</td>
                <td class="cell3">23</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">04</td>
                <td class="cell2">Sit</td>
                <td class="cell3">24</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">05</td>
                <td class="cell2">Amet</td>
                <td class="cell3">25</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">06</td>
                <td class="cell2">Facere</td>
                <td class="cell3">26</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">07</td>
                <td class="cell2">Voluptas</td>
                <td class="cell3">27</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">08</td>
                <td class="cell2">Consequuntur</td>
                <td class="cell3">28</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">09</td>
                <td class="cell2">Nesciunt</td>
                <td class="cell3">29</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">10</td>
                <td class="cell2">Dolorum</td>
                <td class="cell3">30</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
    
        </tbody>
    </table>
    <h2>Member List</h2>
    <hr>
    <table class="list1">
        <thead>
            <tr>
                <th class="head1">No</th>
                <th class="head2">Name</th>
                <th class="head3">Age</th>
                <th class="head4">ID</th>
                <th class="head5">Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="cell1">01</td>
                <td class="cell2">Lorem</td>
                <td class="cell3">21</td>
                <td class="cell4">Lorem</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">02</td>
                <td class="cell2">Magni</td>
                <td class="cell3">22</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">03</td>
                <td class="cell2">Dolor</td>
                <td class="cell3">23</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">04</td>
                <td class="cell2">Sit</td>
                <td class="cell3">24</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">05</td>
                <td class="cell2">Amet</td>
                <td class="cell3">25</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">06</td>
                <td class="cell2">Facere</td>
                <td class="cell3">26</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">07</td>
                <td class="cell2">Voluptas</td>
                <td class="cell3">27</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">08</td>
                <td class="cell2">Consequuntur</td>
                <td class="cell3">28</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">09</td>
                <td class="cell2">Nesciunt</td>
                <td class="cell3">29</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">10</td>
                <td class="cell2">Dolorum</td>
                <td class="cell3">30</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
    
        </tbody>
    </table>
    <h2>Member List</h2>
    <hr>
    <table class="list1">
        <thead>
            <tr>
                <th class="head1">No</th>
                <th class="head2">Name</th>
                <th class="head3">Age</th>
                <th class="head4">ID</th>
                <th class="head5">Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="cell1">01</td>
                <td class="cell2">Lorem</td>
                <td class="cell3">21</td>
                <td class="cell4">Lorem</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">02</td>
                <td class="cell2">Magni</td>
                <td class="cell3">22</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">03</td>
                <td class="cell2">Dolor</td>
                <td class="cell3">23</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">04</td>
                <td class="cell2">Sit</td>
                <td class="cell3">24</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">05</td>
                <td class="cell2">Amet</td>
                <td class="cell3">25</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">06</td>
                <td class="cell2">Facere</td>
                <td class="cell3">26</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">07</td>
                <td class="cell2">Voluptas</td>
                <td class="cell3">27</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">08</td>
                <td class="cell2">Consequuntur</td>
                <td class="cell3">28</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">09</td>
                <td class="cell2">Nesciunt</td>
                <td class="cell3">29</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
            <tr>
                <td class="cell1">10</td>
                <td class="cell2">Dolorum</td>
                <td class="cell3">30</td>
                <td class="cell4">Facere</td>
                <td class="cell5">consectetur adipisicing elit. Minus</td>
            </tr>
    
        </tbody>
    </table>
</div>
    

</body>
</html>
```
