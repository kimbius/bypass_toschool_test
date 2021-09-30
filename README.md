# Bypass Toschool Test

GET EID
```js
const Class = ""; // ชั้น
const Room = ""; // ห้อง

let req = await fetch("https://toschool.in/toschoolsource/php/getExamData.php?tbCode=132&SID=465&Sclass="+Class+"&Sroom="+Room+"&sUrl=toschool_bksc");
let res = await req.json();
for(let obj of res) {
    console.log("%s > EID: %s", obj["title"], obj["test_EID"] || "ไปกดเริ่มทำข้อสอบก่อน")
}
```


เอา EID ที่ได้มาใส่ เพื่อหาคำตอบ
```js
const EID = ""; // EID

await fetch("https://toschool.in/toschoolsource/php/getExamData.php?tbCode=152&curEID=" + EID + "&sUrl=toschool_bksc").then(res => {
    for (let quiz of res.data) {
        let answer = quiz["choice" + (quiz.point.split(",").indexOf("1") + 1)]
        console.log(quiz.quiz_no + ": " + answer);
    }
})
```