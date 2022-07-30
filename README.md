var req = new XMLHttpRequest();
req.open("GET","https://raw.githubusercontent.com/rvsp/restcountries-json-data/master/res-countries.json");
req.send();
req.onload=function(){
  var arr = JSON.parse(req.response);

  //1a
  var asia = arr.filter((ele) => ele.region==="Asia").map((ele) => ele.name);
  console.log(asia);

  //1b
  var pop = arr.filter((ele) => ele.population < 200000).map((ele) => ele.name);
  console.log(pop);

  //1c
  arr.forEach(ele => {
    console.log(ele.name+" "+ele.capital+" "+ele.flag);
  });

  //1d
  const sum = arr.reduce((acc,ele) => {  
    tot = acc + ele.population;
    return tot;
  },0);
  console.log(sum);

  //1e
  var US = arr.filter((ele) => ele.currencies[0].code === "USD").map((ele) => ele.name);
  console.log(US);
}
