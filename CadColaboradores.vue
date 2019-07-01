<template>
  <div class="container">
    <div id="mail-app" class="section">
      <div class="row">
        <div class="col s12">
          <nav class="blue">
            <div class="nav-wrapper">
              <div class="left col s5 m5 l5">
                <ul>
                  <li>
                    <a class="">
                      <i class="material-icons" @click="menuMobile()">menu</i>
                    </a>
                  </li>
                  <li>
                    <label id="lblNomeFun" class="truncate">{{nomeFunc}}</label>
                  </li>
                </ul>
              </div>
              <div class="col s7 m7 l7 ">
              </div>
            </div>
          </nav>
        </div>
        <div class="col s12" style="cursor:pointer;">
          <div id="menuFunc" class="col s1 m4 l4 card-panel z-depth-1">
            <ul class="collection">
              <li class="collection-item avatar" v-bind:style="dadosPessoais" @click="alterMenu(0)">
                <i class="material-icons blue-text" style="position: relative; top: 5px !important;">brightness_high</i>
                <span> Exercício 1</span>
                <p class="truncate grey-text ultra-small">Dados básicos da pessoa</p>
                <a v-if="pend_dadosPessoais > 0" href="#!" class="secondary-content">
                  <span class="new badge blue">pendente</span>
                </a>
                <a v-else  class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar" v-bind:style="documentacao" @click="alterMenu(1)">
                <i class="material-icons green-text" style="position: relative; top: 5px !important;">brightness_high</i>
                <span> Exercício 2</span>
                <p class="truncate grey-text ultra-small">CPF, RG, PIS...</p>
                <a v-if="pend_documentacao > 0" href="#!" class="secondary-content">
                  <span class="new badge blue">pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar" v-bind:style="endereco"  @click="alterMenu(2)">
                <i class="material-icons yellow-text text-darken-3" style="position: relative; top: 5px !important;">brightness_high</i>
                <span > Exercício 3</span>
                <p class="truncate grey-text ultra-small">Precisamos saber onde a pessoa mora</p>
                  <a v-if="pend_endereco > 0" href="#!" class="secondary-content">
                  <span class="new badge blue"> pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar"  v-bind:style="dependentes" @click="alterMenu(3)">
                <i class="material-icons pink-text text-darken-3" style="position: relative; top: 5px !important;">brightness_high</i>
                <span> Exercício 4</span>
                <p class="truncate grey-text ultra-small">Não é obrigatório ter dependentes</p>
                  <a v-if="pend_dependentes > 0" href="#!" class="secondary-content">
                  <span class="new badge blue">pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar" v-bind:style="contratacao" @click="alterMenu(4)">
                <i class="material-icons purple-text text-darken-3" style="position: relative; top: 5px !important;">brightness_high</i>
                <span> Exercício 5</span>
                <p class="truncate grey-text ultra-small">Informações sobre o contrato</p>
                  <a v-if="pend_contratacao > 0" href="#!" class="secondary-content">
                  <span class="new badge blue"> pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar" v-bind:style="sindicato" @click="alterMenu(5)">
                <i class="material-icons indigo-text text-darken-3" style="position: relative; top: 5px !important;">brightness_high</i>
                <span > Exercício 6</span>
                <p class="truncate grey-text ultra-small">Diga mais sobre qual sindicato pertence</p>
                  <a v-if="pend_sindicato > 0" href="#!" class="secondary-content">
                  <span class="new badge blue">pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar" v-bind:style="proventosDesc"  @click="alterMenu(6)">
                <i class="material-icons cyan-text text-darken-3" style="position: relative; top: 5px !important;">brightness_high</i>
                <span > Exercício 7</span>
                <p class="truncate grey-text ultra-small">Informe os detalhes</p>
                  <a v-if="pend_proventosDesc > 0" href="#!" class="secondary-content">
                  <span class="new badge blue">pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
              <li class="collection-item avatar" v-bind:style="complementos" @click="alterMenu(7)">
                <i class="material-icons teal-text text-darken-3" style="position: relative; top: 5px !important;">brightness_high</i>
                <span > Exercício final</span>
                <p class="truncate grey-text ultra-small">Precisamos saber onde a pessoa mora</p>
                  <a v-if="pend_complementos > 0" href="#!" class="secondary-content">
                  <span class="new badge blue">pendente</span>
                </a>
                <a v-else href="#!" class="secondary-content">
                  <span class="new badge green darken-3">OK</span>
                </a>
              </li>
            </ul>
          </div>
<!--Exercicio 1 -->
          <div id="form" v-show ="menuSelected == 0 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 1 -->
<!--Exercicio 2 -->
          <div id="form" v-show ="menuSelected == 1 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 2 -->
<!--Exercicio 3 -->
          <div id="form" v-show ="menuSelected == 2 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 3  -->
<!--Exercicio 4 -->
          <div id="form" v-show ="menuSelected == 3 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 4 -->
<!--Exercicio 5 -->
          <div id="form" v-show ="menuSelected == 4 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 5 -->
<!--Exercicio 6 -->
          <div id="form" v-show ="menuSelected == 5 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 6 -->
<!--Exercicio 7 -->
          <div id="form" v-show ="menuSelected == 6 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 7-->
<!--Exercicio 8 -->
          <div id="form" v-show ="menuSelected == 7 " class="col s12 m7 l8 card-panel">
              <div class="row">
                <div class="col s12 m12 l12" style="padding-left: 15px;">
                 <form class="col s12">
                    <div class="row">
                       <div class="col s12 m12 l12">
                        <label id="lblFiliacaoSind" class>Optante por vale transporte *</label>
                      </div>
                      <div class="col s3 m3 l2" style="padding-left: 25px; padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="S" id="valeTransporteSim" v-model="valeTransporte"/>
                          <label for="valeTransporteSim">Sim</label>  
                      </div>
                      <div class="col s3 m3 l1" style="padding-top: 15px;">
                          <input name="valeTransporte" type="radio" value="N" id="valeTransporteNao" v-model="valeTransporte"/>
                          <label for="valeTransporteNao">Não</label>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col s6 m12 l4">
                        <label id="lblLocalTrabalho">Local de trabalho</label>
                      </div> 
                    </div>
                    <div class="row">
                      <div class="input-field col s6 m2 l2" required="true">
                         <select id="ufTrabalho" ref="ufTrabalho" v-model="ufTrabalho">
                           <option value="" disabled selected>Estado *</option>
                           <option v-for="list in uf" :key="list.uf" v-bind:value="list.uf">{{list.uf}}</option>
                         </select>
                     </div>
                     <div class="input-field col s6 m3 l4" required="true">
                         <select id="cidadeTrabalho" v-model="cidadeTrabalho">
                           <option value="" disabled selected>Selecione a cidade *</option>
                           <option v-for="list in cidadesTrab" :key="list.id_dne_localidade" v-bind:value="list.id_dne_localidade">{{list.nome}}</option>
                         </select>
                     </div> 
                     <div class="col s6 m6 l6">
                        <div class="input-field">
                          <input id="cargosContrato" class="truncate"  type="text" v-model="cargoCbo" disabled>
                          <label for="cargosContrato" >Cargo do colaborador </label>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                     <div class="col s12">
                       <label id="lblDescCargo" for="descCargo"> Descreva aqui as atribuições relacionadas ao cargo *</label> 
                        <textarea id="descCargo" name="descCargo" rows="3" cols="53" v-model="descCargo" maxlength="400">      
                        </textarea> 
                        </div>
                    </div>
                 </form>
              </div>
            </div>
            <div class="center">
              <div class="row" style="padding-top: 50px;">
                <a class="btn waves-effect waves-light gradient-45deg-light-blue-cyan" @click="enviarContrato()" >Salvar e continuar</a>
              </div>
            </div>
          </div>
<!-- fim Exercicio 8 -->
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapState, mapActions} from 'vuex';
import {TheMask} from 'vue-the-mask';
import {Money} from 'v-money';
import {mask} from 'vue-the-mask'; 

export default {
  components: {Money,TheMask},
  name: 'nfConsultar',
  directives: {mask},
  data () {
    return {
      menuCheck: false,
      money: {
        decimal: ',',
        thousands: '.',
        prefix: ' R$ ',
        suffix: '',
        precision: 2,
        masked: false
      },

      // dados pessoais
      nomeFunc: '',
      dataNasc: '',
      emailFunc: '',
      eCivil: '',  
      sexo: '',
      nomeMae: '',
      nomePai: '',
      numeroTel: '',

      // documentação
      cpf: '',
      tituloEleitor: '',
      rg: '',
      ufEmissorRg: '',
      orgaoEmissorRg: '',
      dataExpRg: '',
      pis: '',
      ctps: '',
      serie: '',
      ufEmissorCtps: '',

      // endereço
      cepEnd: '',
      logradouroEnd: '',
      numeroEnd: '',
      complementoEnd: '',
      bairroEnd: '',
      ufEnd: '',
      localidadeEnd: '',

      // dependentes
      dependentesTable:[],
      dependentes:'',
      nomeDependente: '',
      cpfDependentes: '',
      dataNascDependente: '',
      tipoDependente: '',
 
      // contratação
      id_func_contrato: 0,
      dataAdmissaoFunc: '',
      salarioFunc: '',
      tipoAdmissao: '',
      areaFunc: '',
      matriculaFunc: '',
      ufTrabalho: '',
      cidadeTrabalho: '',
      valeTransporte: 'N',
      cargosContrato: '',
      cargoCbo: '',
      descCargo: '',

      // sindicato
      sindicatoId: '',
      aceiteSindicatoFiliacao: 'N',
      contribuiuSindicatoFiliacao: 'N',
      valorContribuicao: '',

      // proventos/descontos
      provFixo: false,
      descProventos: '',
      qtdProvento: '',
      tipoProvento: '',
      valorProvento: '',
      undadeProvento: 'un.',

      // complementos
      etnia: '',
      gInstrucao: '',
      chegadaPais: '',
      nacionalidades: [],
      necessidadeEspecial: 'N',
      necessidadeEspecialSel: '',
      nacionalidade:'',
      naturalidadeUf: '',
      cidadeNaturalidade: '',
      
      // dados do menu
      menuSelected: 0 ,

      dadosPessoais: '',
      documentacao: '',
      endereco: '',
      dependentes: '',
      contratacao: '',
      sindicato: '',
      proventosDesc: '',
      complementos: '',

      pend_dadosPessoais: 1,
      pend_documentacao: 1,
      pend_endereco: 1,
      pend_dependentes: 1,
      pend_contratacao: 1,
      pend_sindicato: 1,
      pend_proventosDesc: 1,
      pend_complementos: 1,

    }
  },
   mounted() { 
     this.alterMenu(0);
     this.carregaSelects();
  },
  updated() {
    $(document).ready(function(){
      Materialize.updateTextFields();      
    }); 
  },

  methods: {
    // Necessário para manipular valor dos selects
    carregaSelects: function(event){    
      var self = this;
      $(document).ready(function() {

        $('#tipoDependente').change(function() {
          var varURL = $("option:selected", this).val();
          self.tipoDependente = varURL;
        });
        $('#eCivil').change(function() {
          var varURL = $("option:selected", this).val();
          self.eCivil = varURL;
        });
        $('#tipoAdmissao').change(function() {
          var varURL = $("option:selected", this).val();
          self.tipoAdmissao = varURL;
        });
        $('#ufTrabalho').change(function() {
          var varURL = $("option:selected", this).val();
          self.ufTrabalho = varURL;
          self.carregaCidadesContratacao(varURL);
        });
        $('#cidadeTrabalho').change(function() {
          var varURL = $("option:selected", this).val();
          self.cidadeTrabalho = varURL;
        });
        $('#descProventos').change(function() {
          var varURL = $("option:selected", this).val();
          self.descProventos = varURL;
          self.altreraTipoUnProv(self.descProventos); 
        });
        $('#etnia').change(function() {
          var varURL = $("option:selected", this).val();
          self.etnia = varURL;
        });
        $('#gInstrucao').change(function() {
          var varURL = $("option:selected", this).val();
          self.gInstrucao = varURL;
        });
        $('#naturalidadeUf').change(function() {
          var varURL = $("option:selected", this).val();
          self.naturalidadeUf = varURL;
          self.carregaCidadesComplementos(varURL);
        });
        $('#cidadeNaturalidade').change(function() {
          var varURL = $("option:selected", this).val();
          self.cidadeNaturalidade = varURL;
        });
        $('#nacionalidade').change(function() {
          var varURL = $("option:selected", this).val();
          self.nacionalidade = varURL;
        });
        $('#necessidadeEspecialSel').change(function() {
          var varURL = $("option:selected", this).val();
          self.necessidadeEspecialSel = varURL;
        });
        $('#dataAdmissaoFunc').change(function() {
          var varURL =  document.getElementById("dataAdmissaoFunc").value
          self.dataAdmissaoFunc = varURL;
        });
        $('#dataNasc').change(function() {
          var varURL =  document.getElementById("dataNasc").value
          self.dataNasc = varURL;
        });
        $('#dataNascDependente').change(function() {
          var varURL =  document.getElementById("dataNascDependente").value
          self.dataNascDependente = varURL;
        });
        $('#dataExpRg').change(function() {
          var varURL =  document.getElementById("dataExpRg").value
          self.dataExpRg = varURL;
        });
        $('#ufEmissorRg').change(function() {
          var varURL =  document.getElementById("ufEmissorRg").value
          self.ufEmissorRg = varURL;
        });
        $('#ufEmissorCtps').change(function() {
          var varURL =  document.getElementById("ufEmissorCtps").value
          self.ufEmissorCtps = varURL;
        });
        $('#sindicatoId').change(function() {
          var varURL =  document.getElementById("sindicatoId").value
          self.sindicatoId = varURL;
        });

      });
    },
    // Necessario para atualizar os selects
    ativaSelects: function(){
      $(document).ready(function(){
        $('#eCivil, #ufEmissorCtps, #sindicatoId, #tipoDependente, #tipoAdmissao, #ufTrabalho, #cidadeTrabalho, #descProventos, #etnia, #gInstrucao, #naturalidadeUf, #ufEmissorRg, #cidadeNaturalidade, #nacionalidade, #necessidadeEspecialSel ').material_select();
      });
    },
  
    alterMenu: function(menu){
      this.dadosPessoais = '';
      this.documentacao = '';
      this.endereco = '';
      this.dependentes = '';
      this.contratacao = '';
      this.sindicato = '';
      this.proventosDesc = '';
      this.complementos = '';
      this.menuSelected = menu; 
        if(menu == 0){
          this.dadosPessoais = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
        if(menu == 1){
          this.documentacao = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
        if(menu == 2){
          this.endereco = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
        if(menu == 3){
          this.dependentes = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
        if(menu == 4){
          this.contratacao = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
        if(menu == 5){
          this.sindicato = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
        if(menu == 6){
          this.proventosDesc = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          };
          this.menuMobile();
        }
        if(menu == 7){
          this.complementos = { 
            'background': '#e1f5fe',
            'border-left': '4px solid #29b6f6',
          }
          this.menuMobile();
        }
      
      this.ativaSelects();
    },
    menuMobile: function(){
      var menuLateral = document.getElementById("menuFunc");
      menuLateral.classList.toggle('toggleMenu');
    }
  }
}                                           
</script>
<style>
#descCargo {
  height: 100px;
  padding: 10px;
  line-height: 1.5;
  border-radius: 5px;
  border: 1px solid #ccc;
  box-shadow: 1px 1px 1px #999;
}
#select{
  position: relative;
  top: -7px !important;
} 
#lblFixo{
  position: relative;
  top: 10px !important;
  font-size: 16px;
} 
#provFixo{
  padding-top: 5px;
} 
#inputMoney{
  position: relative;
  top: 13.9px !important;
} 
#lblLocalTrabalho{
  font-size: 20px;
  position: relative;
  top: 10px !important;
}
#lblNomeFun{
  font-size: 16px;
  color: white;
}
#undadeProvento{
  font-size: 18px;
  position: relative;
  left: -18px !important;
}
#lblDescCargo{
  font-size: 18px;
}
#lblFiliacaoSind{
  font-size: 20px;
}
#form{
  margin: 0;
  height: 694px;
  padding-top: 25px; 
}
span.badge.new:after {
  content: "";
}
nav ul a.btn, nav ul a.btn-large, nav ul a.btn-large, nav ul a.btn-flat, nav ul a.btn-floating {
  margin-left: 0px;
  margin-right: 0px;
}
#menuFunc {
	margin: 0;					
}
.collection .collection-item.avatar {
  min-height: 84px;
  padding-left: 20px;
  position: relative;
}
.collection {
  border: none;
  width: 105%;
  position: relative;
  left: -11px;
}

/* Tamanho dos components de acordo com a resolução  */
@media (max-width: 993px) and (min-width: 677px){
  #form{
    margin: 0;
    width: 66.5%;
    padding-top: 25px; 
  }
}
@media (max-width: 678px) {
  #form{
    margin: 0px;
    width: 99.5%;
    height: 844px;
    padding-top: 25px; 
  }
  #menuFunc{
    background-color: azure;
    width:280px;
    position: absolute;
    left: -315px ;
    overflow: hidden;
    transition: all .3s;
    z-index:99;
  }
  .toggleMenu{
    position: absolute;
    left: 15px !important;
    overflow: hidden;
    transition: all .3s;
    z-index:99;
  }
  #lblNomeFun{
    font-size: 0px;
    color: #2196F3;
  }
}  

</style>