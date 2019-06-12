---
layout: post
title: Họa Mi Hót's birthday
tags: [birthday]
---
<style>
    .active{
        color: 	#49974b;
    }
    .prepare{
        color: 	#17a2b8;
    }
</style>
<table id="date-table" style="width:100%">
    <caption>Hoa mi hot's birthday</caption>
    <tr>
        <th>Name</th>
        <th>Birthday</th> 
        <th>Phone</th>
    </tr>
    <tbody id="rows">

    </tbody>
</table>

<script>
    let now = new Date();
    let now_month_date = String(now.getMonth() + 1).padStart(2, '0') + String(now.getDate()).padStart(2, '0');
    let now_month = String(now.getMonth() + 1).padStart(2, '0');
    let next_month = String(now.getMonth() + 2).padStart(2, '0');
    let people = [
    {name: 'Phùng Văn Thành', birthday: '9/6/1996', phone: '0388015607'},
    {name: 'Đặng Khắc Toàn', birthday: '21/11/1996', phone: '0364176683'},
    {name: 'Vũ Đại Phong', birthday: '30/4/1995', phone: '0363830369'},
    {name: 'Lâm Văn Thịnh', birthday: '6/4/1996', phone: '0376564312'},
    {name: 'Đặng Ngọc Sơn', birthday: '3/6/1994', phone: '0396747724'},
    {name: 'Mai Duy Thanh', birthday: '10/5/1995', phone: '0375787324'},
    {name: 'Nguyễn Thị Thủy', birthday: '12/11/1996', phone: '0354064724'},
    {name: 'Phạm Thu Trang', birthday: '19/03/1996', phone: '0328695658'},
    {name: 'Mai Hồng Anh', birthday: '31/11/1997', phone: '0983801481'},
    {name: 'Lê Hồng Hạnh', birthday: '26/10/1997', phone: '0395416890'}
    ];
    people.map(function(p){
    let dataSplited = p.birthday.split('/');
    p.birthday = new Date(dataSplited[2], dataSplited[1], dataSplited[0]);
    
    return p
    });

    people.sort(function(p1, p2){
    let m1 = String(p1.birthday.getMonth()).padStart(2, '0');
    let d1 = String(p1.birthday.getDate()).padStart(2, '0');
    let m2 = String(p2.birthday.getMonth()).padStart(2, '0');
    let d2 = String(p2.birthday.getDate()).padStart(2, '0');
    return (m1+d1) - (m2+d2);
    });

    people.map(function(p){
    let y = p.birthday.getFullYear();
    let m = String(p.birthday.getMonth()).padStart(2, '0');
    let d = String(p.birthday.getDate()).padStart(2, '0');

    if(now_month > m){
        p.name = '<span>&#10004;</span> ' + p.name;
    }else if(now_month ==  m){
        p.name = '<span class="active">&#127919;</span> ' + p.name;
    }else{
        if(next_month == m){
            p.name = '<span class="prepare">&#9971;</span> ' + p.name;
        }
    }    
    p.birthday = d + '/' + m + '/' + y;
    return p;
    })
    let rows = "";
    rows = people.reduce(function(tmp, p){
        return tmp + '<tr><td>' + p.name + '</td><td>' + p.birthday + '</td><td>' + p.phone + '</td></tr>'; 
    }, "");
    document.getElementById("rows").innerHTML += rows;
</script>