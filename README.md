# regex
Slides

//var regVeriEmail = /jony.nunes@fatec.sp.gov.br/;
     //var regVeriEmail = /^jony.nunes@fatec.sp.gov.br/;  //tem que começar com o mesmo parâmetro
      var regVeriEmail = /jony.nunes@fatec.sp.gov.br$/; //tem que terminar com o mesmo parâmetro

      //console.log(regVeriEmail.exec(this.nomeDependente)) // mostra detalhes de onde encontrou a  
      //console.log(regVeriEmail.exec(this.nomeDependente).index) // pega o endereço da primeira string onde encontrou a variável 

      console.log(regVeriEmail.test(this.nomeDependente)) //retorna true ou false

      // if(regVeriEmail.test(this.nomeDependente)){
      //   console.log("true")
      // }else{
      //   console.log("false")
      // }
