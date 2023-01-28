var tableId = "table-2";
var table = document.getElementById(tableId);
let btnReadDocument = document.querySelector('#Document')
let input1Document = document.querySelector('#file-input-1')
let input2Document = document.querySelector('#file-input-2')
let btnCalc = document.querySelector('#calcular')
let btnExport = document.querySelector('#exportar')
let mes = document.querySelector('#mes')
let mesValue
let dados = document.querySelector('.dados')
let mesInput = document.querySelector('#mesInput')


let checkAll = () =>{
    for (let i = 4; i < 8; i++) {
      checkBase(i)
      
    }



}
let checkBase = (a) =>{

  let s = 0



  
  let firstCol = document.querySelectorAll(`table tr td:nth-child(${a})`)
  firstCol.forEach((Fcol)=>{
  let lineText = Fcol.innerHTML

  if (s==0) {
    s=1
  } else {
    if (lineText.charAt(0)=="-") {
  Fcol.style.color="red"

  } else {
  Fcol.style.color="green"  
  }
  }
  

  })


}
let checkUndefined = (a) =>{
  let firstCol = document.querySelectorAll(`table tr td:nth-child(${a})`)
  firstCol.forEach((Fcol)=>{



    if (Fcol.innerHTML=="undefined") {
      
    Fcol.innerHTML = "00:00:00"









    } else {
      
    }



  })

}
let LineColor = () =>{


    let lineInit = false
    let i = 0
    let lines = document.querySelectorAll('tr')



    lines.forEach((line)=>{
    if (lineInit==false) {
      lineInit=true
    } else {
      
      if(i==1){
    line.style.padding="20px"
    line.style.backgroundColor="rgba(210, 210, 210)"


      i=0
      }else{



      i=1
      }
    }



    })


}

let SelecionarArquivos = () =>{
    mesValue = mes.value

    if (mesValue=="") {
      alert('Insira o mes')
    } else if(mesValue>0 && mesValue<=12) {
      dados.style.display="block"
      mesInput.style.display="none"



    }else{
        alert('Mes Invalido')



    }

}
// Lista de objetos que será preenchida com os dados dos arquivos
var list = [];
var mergedList = [];
function readAndMergeFiles() {

    dados.style.display="none"
    btnReadDocument.style.display="none"
    input1Document.style.display="none"
    input2Document.style.display="none"
  readFile(1, 'file-input-1', list);
  readFile(2, 'file-input-2', list);
  

  
  




  setTimeout(()=>(  mergedList.forEach((objecto)=>{addObjectToTable(objecto)})), 2000)
  setTimeout(()=>{
    btnCalc.style.display="block"}, 2000)


    setTimeout(()=>{

    LineColor()

    checkUndefined(7)
    checkUndefined(6)
    checkUndefined(5)
    checkUndefined(4)
    checkUndefined(3)


    checkAll()


    }, 2000)
}

function readFile(num, fileName, list) {
  var input = document.getElementById(fileName);

  var file = input.files[0];


  // Cria um novo FileReader
  var reader = new FileReader();




  // Lê o arquivo como texto
  reader.readAsText(file);  

  let i = 1;
  // Executa uma função quando o arquivo for lido
  reader.onload = function() { 


    // O conteúdo do arquivo é armazenado em "result"
    var result = reader.result;    
    
    
    
    
   // console.log(reader.result)
    // Aqui você pode manipular o conteúdo do arquivo, por exemplo,
    // dividindo-o em linhas e colunas e adicionando os dados à tabela
    addDataToTable(result, fileName, list);
  };
}

function addDataToTable(data, fileName, list) {



  console.log(fileName)
  // Divide o conteúdo do arquivo em linhas
  var rows = data.split("\n");
 if (fileName=='file-input-2') {
  console.log('input 2')
 } else {
  console.log('input 1')
 }
  // Pega a tabela especificada pelo parâmetro "tableId"
  var table = document.getElementById(tableId);
    console.log()
  // Para cada linha do arquivo...
  for (var i = 1; i < rows.length; i++) {
    // Divide a linha em colunas
    var cols = rows[i].split(";");
     //console.log(rows[i])
    // Cria um novo objeto para armazenar os dados da linha
    var obj = {};


  

    // Se o arquivo for o primeiro, adiciona os dados de Cracha, Nome e SaldoMes ao objeto
    if (fileName == 'file-input-1') {

      obj['Cracha'] = cols[1];
      obj['Nome'] = cols[2];
      obj['SaldoMes'] = cols[6];
 
    //console.log(obj['Cracha'])
    
    } else {
      // Se o arquivo for o segundo, adiciona os dados de SaldoVenc3, SaldoVenc2, SaldoVenc1 e SaldoVencido ao objeto
      obj['SaldoVenc3'] = cols[2];
      obj['SaldoVenc2'] = cols[3];
      obj['SaldoVenc1'] = cols[4];
      obj['SaldoVencido'] = cols[5];
      obj['Cracha'] = cols[0]
      obj['Nome'] = cols[1]
       


      }
      
      // Adiciona o objeto à lista
    //console.log(obj)  
    list.push(obj);   

//console.log(list)
  

// Para cada objeto da lista...
for (var a = 0; a < list.length; a++) {
  // Pega o objeto atual
  var obj = list[a];

  // Se o objeto já existir na lista mesclada...
  if (mergedList.some(function(e) { return e.Cracha == obj.Cracha })) {
    
    // Pega o índice do objeto na lista mesclada
    var index = mergedList.findIndex(function(e) { return e.Cracha == obj.Cracha });

    // Pega o objeto na lista mesclada
    var mergedObj = mergedList[index];
  
    // Se o objeto atual tiver propriedades que o objeto mesclado não tem,
    // adiciona essas propriedades ao objeto mescla
    if (obj.hasOwnProperty('Nome')) mergedObj['Nome'] = obj['Nome'];
    if (obj.hasOwnProperty('SaldoMes')) mergedObj['SaldoMes'] = obj['SaldoMes'];
    if (obj.hasOwnProperty('SaldoVenc3')) mergedObj['SaldoVenc3'] = obj['SaldoVenc3'];
    if (obj.hasOwnProperty('SaldoVenc2')) mergedObj['SaldoVenc2'] = obj['SaldoVenc2'];
    if (obj.hasOwnProperty('SaldoVenc1')) mergedObj['SaldoVenc1'] = obj['SaldoVenc1'];
    if (obj.hasOwnProperty('SaldoVencido')) mergedObj['SaldoVencido'] = obj['SaldoVencido'];
  } else {
    // Se o objeto não existir na lista mesclada, adiciona-o à lista
    mergedList.push(obj)
  }











}}


}
console.log(mergedList)




// Adiciona um objeto à tabela
function addObjectToTable(obj) {
  // Pega a tabela especificada pelo parâmetro "tableId"
  var table = document.getElementById(tableId);

  // Cria uma nova linha
  var row = table.insertRow();

  // Adiciona células à linha
  var cell1 = row.insertCell(0);
  var cell2 = row.insertCell(1);
  var cell3 = row.insertCell(2);
  var cell4 = row.insertCell(3);
  var cell5 = row.insertCell(4);
  var cell6 = row.insertCell(5);
  var cell7 = row.insertCell(6);
  var cell8 = row.insertCell(7)


  // Atribui os valores dos campos do objeto às células
  cell1.innerHTML = obj['Cracha'];
  cell2.innerHTML = obj['Nome'];
  cell3.innerHTML = obj['SaldoMes'];
  cell4.innerHTML = obj['SaldoVenc3'];
  cell5.innerHTML = obj['SaldoVenc2'];
  cell6.innerHTML = obj['SaldoVenc1'];
  cell7.innerHTML = obj['SaldoVencido'];
  cell8.innerHTML = mesValue

}

// Para cada objeto da lista...
for (var i = 0; i < list.length; i++) {
  // Adiciona o objeto à tabela
  addObjectToTable(list[i]);
}


function Calcular(){



  btnCalc.style.display="none"
  btnExport.style.display="block"
        CalcularSaldos()

        setTimeout(()=>{
          checkAll()



        }, 4000)
        


}


function CalcularSaldos(){

    
    let tr = document.querySelectorAll('tr')
    let Atual = document.querySelectorAll('table tr td:nth-child(3)')
    let Venc3 = document.querySelectorAll('table tr td:nth-child(4)')
    let Venc2 = document.querySelectorAll('table tr td:nth-child(5)')
    let Venc1 = document.querySelectorAll('table tr td:nth-child(6)')
    let Vencido = document.querySelectorAll('table tr td:nth-child(7)')
      let nTime = '00:00:00'
      let ConteudoVenc1_Reserva = []
      let verifica = []

      let completa = []
      for (let index = 0; index < Venc1.length; index++) {
        ConteudoVenc1_Reserva[index] = calcularSegundos(Venc1[index].innerHTML)
        verifica[index] = calcularSegundos(Venc1[index].innerHTML)
        completa[index] = calcularSegundos(Venc1[index].innerHTML)

      }
    setTimeout(()=>{   
      
      

      for (let index = 1; index < Atual.length; index++) {

    let ConteudoAtual = calcularSegundos(Atual[index].innerHTML)
    let ConteudoVenc1 = calcularSegundos(Venc1[index].innerHTML)
    
    let ConteudoVenc2 = calcularSegundos(Venc2[index].innerHTML)
    let ConteudoVenc3 = calcularSegundos(Venc3[index].innerHTML)
    let calculadon3 = ConteudoAtual + ConteudoVenc1
    let calculadon2
    let calculadon1
    
    if (ConteudoAtual>0) {


      if (ConteudoVenc1>0) {


        //Venc3[index].innerHTML = calcularHora(ConteudoAtual)
         
        
      } 
      
      
      
      else if(ConteudoVenc1<0) {

    
        if (ConteudoVenc2==0 && ConteudoVenc3==0) {
          calculadon2 = 0
          calculadon1 = 0

        } else {
        calculadon2 = calculadon3 + ConteudoVenc2
        calculadon1 = calculadon2 + ConteudoVenc3
          
        }

        if (calculadon3>0) {

          Venc1[index].innerHTML = nTime

          

            if (calculadon2>0) {
              Venc2[index].innerHTML = nTime
            
              verifica[index] = "NO"
              completa[index] = calcularHora(calculadon1) 



            } else if(calculadon2<0){
              Venc2[index].innerHTML = calcularHora(calculadon2)
            } else if(calculadon2==0){

          console.log(`ConteudoAtual ${calcularHora(ConteudoAtual)}`)
          verifica[index] = "NO"
          completa[index] = calcularHora(calculadon3)

            }

      






        } else if(calculadon3<=0){
          Venc1[index].innerHTML = calcularHora(calculadon3)
        }
            





      }
      else if(ConteudoVenc1==0){
          if (ConteudoVenc2==0) {



            console.log(`Caso 0 1 00 00 ${calcularHora(ConteudoAtual)}`)
            // 0 1 00 00
            calculadon1 = ConteudoAtual + ConteudoVenc3
            if (calculadon1==0) {
              Venc3[index].innerHTML = nTime
            } else if(calculadon1>0){
              verifica[index] = "NO"

              completa[index] = calcularHora(calculadon1)
              
            } else if(calculadon1<0){

              Venc3[index].innerHTML = calcularHora(calculadon1)

            }










          } else if(ConteudoVenc2<0){
              calculadon2 = ConteudoAtual + ConteudoVenc2
              if (calculadon2<0) {



                verifica[index] = "Calculado"
                Venc2[index].innerHTML = calcularHora(calculadon2)
              } else if(calculadon2>0){



                Venc2[index].innerHTML = nTime
                if (ConteudoVenc3<0) {
                  calculadon1 = calculadon2 + ConteudoVenc3

                  if (calculadon1) {
                    
                  } else {
                    
                  }
                } else if(ConteudoVenc3 == 0){
                  verifica[index] = "NO"
                  completa[index] = calcularHora(calculadon2)



                }
              }


            // 0 00 1 00
          } else if(ConteudoVenc2>0){




          }



      }
      
    } 
    
    














    
    if(ConteudoAtual<0) {
      if (ConteudoVenc1<0) {
        
        //console.log(`Entrou <0 ${calcularHora(ConteudoAtual)}`)
       // Venc3[index].innerHTML = calcularHora(ConteudoAtual)
      } else if(ConteudoVenc1>0){

        //console.log(`Entrou >0 ${calcularHora(ConteudoAtual)}`)
  

        if (calculadon3>0) {
          Venc1[index].innerHTML = calcularHora(calculadon3)
        } else if(calculadon3<0){
          Venc1[index].innerHTML = nTime



          
                      calculadon2 = calculadon3 + ConteudoVenc2
          

          console.log(`ConteudoVenc1 ${ConteudoVenc1} ConteudoAtual ${ConteudoAtual}`)
          console.log(`calculadon2${calculadon2} = calculadon3${calculadon3} + ConteudoVenc2${ConteudoVenc2}`)
          calculadon1 = calculadon2 + ConteudoVenc3
          console.log(`calculadon1${calculadon1} = calculadon2${calculadon2} + ConteudoVenc3${ConteudoVenc3}`)
          if (calculadon2>0) {
            Venc2[index].innerHTML = calcularHora(calculadon2)

            
          } else if(calculadon2<0){
            
            Venc2[index].innerHTML = nTime

            verifica[index] = "NO"
            completa[index] = calcularHora(calculadon1)


          }

        }
        
      }
        else if(ConteudoVenc1==0){
          if (ConteudoAtual=='-27000') {
            console.log('Delaine')
          } else {
            
          }
      
            if (ConteudoVenc2==0) {
              if (ConteudoAtual=='-27000') {
                console.log('Delaine ConteudoVenc2 == 0')
              } else {



              }


            
                if (ConteudoVenc3==0) {
                  if (ConteudoAtual=='-27000') {
                    console.log('Delaine ConteudoVenc3 == 0')
                  } else {



                  }
  
              } else if(ConteudoVenc3>0){
                  verifica[index] = "NO"
                  completa[index] = calcularHora(ConteudoAtual + ConteudoVenc3)
                  Venc2[index].innerHTML = nTime
                  Venc3[index].innerHTML = nTime

  
                // 1 0 00 00
              }
            } else if(ConteudoVenc2>0){
              // 1 0 0 00
                   
            
let contValue = ConteudoAtual + ConteudoVenc2

              if (ConteudoVenc1==0) {
                
                   if (contValue<0) {
                    verifica[index] = "NO"
                    completa[index] = calcularHora(contValue)
          
                   } else {
                    Venc2[index] = calcularHora(contValue)
                   }
              } else {
                
              }








                cont0102 = ConteudoAtual + ConteudoVenc2
          
                if (ConteudoAtual=='-27000') {
                  console.log('Delaine ConteudoVenc2 > 0')
                  console.log(`${calcularHora(cont0102)}`)



                } else {
                
                }         
                
                






                if (cont0102<0) {                
                  Venc1[index].innerHTML = nTime

                  Venc2[index].innerHTML = nTime
                  let cont0101 = cont0102 + ConteudoVenc3
                  if (cont0101 < 0) {
                    verifica[index] = "NO"
                    completa[index] = calcularHora(cont0101)
                    Venc3[index].innerHTML = nTime
                  } else {
                    
                  Venc3[index].innerHTML = calcularHora(cont0101)
                  }
                  
                  if (ConteudoAtual=='-27000') {
                  console.log('Delaine cont0102 < 0')
                } else {
                
                }            
                  if (ConteudoVenc1>0) {
                    cont0101=cont0102 + ConteudoVenc3
                    if (ConteudoAtual=='-27000') {
                      console.log('Delaine ConteudoVenc1 > 0')
                    } else {
                    
                    }


              
                  } else if(ConteudoVenc1<0){
                  
                  }


                } else {
              verifica[index]="Calculado"
              Venc2[index].innerHTML = calcularHora(cont0102)              
                }
              



            }



        }



















      
    }
    if(isNaN(ConteudoAtual)){
        console.log('unde')



    }

    //Atual[index].innerHTML = nTime
  }}, 10)



    setTimeout(()=>{
    console.log(tr[i])
    console.log(Venc1.length)
    for (let index = 1; index < Venc1.length; index++) {
      Vencido[index].innerHTML = Venc1[index].innerHTML



    }



    }, 100)

    setTimeout(()=>{

    for (let index = 1; index < Venc2.length; index++) {
    
      Venc1[index].innerHTML = Venc2[index].innerHTML

      
    }








    },200)
  setTimeout(()=>{
    for (let index = 1; index < Venc3.length; index++) {
      Venc2[index].innerHTML = Venc3[index].innerHTML
      
    }




  }, 400)

  setTimeout(()=>{
    for (let index = 1; index < Venc3.length; index++) {
      Venc3[index].innerHTML = '00:00:00'
      
    }



  },600)

  setTimeout(()=>{



    for (let index = 1; index < Venc3.length; index++) {
  
    let ConteudoAtual = calcularSegundos(Atual[index].innerHTML)

    console.log(ConteudoVenc1_Reserva)
    if (verifica[index]=="NO") {

      Venc2[index].innerHTML = nTime
      Venc3[index].innerHTML = completa[index]
    } else {

      if (verifica[index]=="Calculado") {

        
          
      } else {
             if (ConteudoAtual>=0 && ConteudoVenc1_Reserva[index]>=0) {


          Venc3[index].innerHTML = calcularHora(ConteudoAtual)
          } else if (ConteudoAtual<0 && ConteudoVenc1_Reserva[index]<=0) {
            Venc3[index].innerHTML = calcularHora(ConteudoAtual) 
          }     
      }

    }

    



 
    }
 



  },1200)



}



let calcularSegundos = (hora) =>{
  let sinal = hora.charAt(0)
  
  
  let horaCerta
  
  if (sinal=='-') {
    
  horaCerta = hora.substring(1)
  } else {
  horaCerta = hora
  }
  let partesDaHora = horaCerta.split(":")
  partesDaHora[0] = parseInt(partesDaHora[0] * 3600)
  partesDaHora[1] = parseInt(partesDaHora[1] * 60)
  partesDaHora[2] = parseInt(partesDaHora[2])

  let segundos = (partesDaHora[0] + partesDaHora[1] + partesDaHora[2])

  if (sinal == '-') {
    segundos = -segundos
  } else{
    
  }


  return segundos
  
}


let calcularHora = (d) =>{
  if (d < 0) {
    d = Math.abs(d);
    var h = Math.floor(d / 3600);
    var m = Math.floor(d % 3600 / 60);
    var s = Math.floor(d % 3600 % 60);
    return "-" + (h < 10 ? "0" + h : h) + ":" + (m < 10 ? "0" + m : m) + ":" + (s < 10 ? "0" + s : s);
  } else {
    var h = Math.floor(d / 3600);
    var m = Math.floor(d % 3600 / 60);
    var s = Math.floor(d % 3600 % 60);
    return (h < 10 ? "0" + h : h) + ":" + (m < 10 ? "0" + m : m) + ":" + (s < 10 ? "0" + s : s);
  }




}

let verificaSaldo = () =>{




}

let n = calcularHora(-9300)
console.log(`Hora: ${n}`)