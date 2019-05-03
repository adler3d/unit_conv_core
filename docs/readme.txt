var get_UDS2Aluminium=(USD2LPG,LPG2MJ,MJ2Aluminium)=>{
  var USD2MJ=USD2LPG*LPG2MJ;
  var UDS2Aluminium=USD2MJ*MJ2Aluminium;
  return UDS2Aluminium;
}

var EURO2USD=1.12;var USD2EURO=1.0/EURO2USD;
var EURO_per_LPG=[0.691,0.241];
var USD_per_LPG=EURO_per_LPG[0]*EURO2USD;
var MJ_per_Aluminium=[46.8,54];
var MJ_per_LPG=46.1;
var USD_per_A=1.0/get_UDS2Aluminium(1.0/USD_per_LPG,1.0/MJ_per_LPG,1.0/MJ_per_Aluminium[1]);
USD_per_A;

var arr=[];
var D1=(inp,out)=>{arr.push([inp,out]);};
var D2=(inp,out)=>{D1(inp,out);D1(out,inp);};

D2({usd:1.1204},{euro:1.0});
D2({euro:0.691},{LPG_L:1.0}); //or 0.241
D2({LPG_KG:1.0},{LPG_L:1.96}); //or 1.75

D1({LPG_KG:1.0},{MJ:46.8});

D1({MJ:46.1},{Aluminium:1.0});
//D1({LPG_KG:1.0},{MJ:54});



usd->euro->LPG_L->LPG_KG->MJ->Aluminium

1.0/1.1204*
1.0/0.691*
1.0/1.96*
46.8*
1.0/46.1
// 0.6690178554088286

D1({usd:0.81},{Aluminium_lb:1.0});
D1({Aluminium_lb:1.0},{Aluminium_kg:0.453592});

usd->Aluminium_lb->Aluminium_kg
1.0/0.81*
0.453592
// 0.5599901234567901
