<template>
    <div class="nav bg-light-emphasis d-flex   offcanvas show" :class="{ 'collapsed': isCollapsed }" data-bs-scroll="true" data-bs-backdrop="false" tabindex="-1" id="offcanvasScrolling" aria-labelledby="offcanvasScrollingLabel">
        <div class="offcanvas-body">
                <ul class="list-group-flush container d-block ">
                    <a class="nav-route text-decoration-none" href="/" aria-current="true">
                        <div class="nav-container item-bg text-dark-emphasis py-2">
                            <IconsHome />
                            <span class="list-group-item">Home</span>
                        </div>
                    </a>
                    <a class="nav-route text-decoration-none" href="/controle-de-acesso" aria-current="true">
                        <div class="nav-container item-bg text-dark-emphasis py-2">
                            <IconsControl />
                            <span class="list-group-item">Controle de Acesso</span>
                        </div>
                    </a>
                    <a class="nav-route text-decoration-none" href="/inventario" aria-current="true">
                        <div class="nav-container item-bg text-dark-emphasis py-2">
                            <IconsSpreadSheet />
                            <span class="list-group-item">Inventário</span>
                        </div>
                    </a>
                    <a class="nav-route text-decoration-none" href="/configuracoes-de-inventario" aria-current="true"> 
                        <div class="nav-container item-bg text-dark-emphasis py-1">
                            <IconsOrganizingTables />
                            <span class="list-group-item">Organizar Inventário</span>
                        </div>
                    </a>
                    <a class="nav-route text-decoration-none" href="/registro" aria-current="true">
                        <div class="nav-container item-bg text-dark-emphasis py-2">
                            <IconsDirectory />
                            <span class="list-group-item">Registro</span>
                        </div>
                    </a>
                    <a class="nav-route text-decoration-none" href="/configuracoes" aria-current="true">
                        <div class="nav-container item-bg text-dark-emphasis py-2">
                        <IconsSettings width="25px" height="25px"/>
                            <span class="list-group-item">Configurações</span>
                        </div>
                    </a>
                    <a class="nav-route text-decoration-none" href="/sobre" aria-current="true">
                        <div class="nav-container item-bg d-inline-block text-start text-dark-emphasis py-2">
                            <IconsInformation />
                            <span class="d-inline-block list-group-item">Sobre</span>
                        </div>
                    </a>
                </ul>
            </div>
            <div class="offcanvas-footer d-block">
                <button class="colapse-btn d-flex align-items-center justify-content-center btn bg-gray-light text-dark" @click="sidebarColapse" type="button" id="sideBareColapse" >
                    <IconsCloseArrow :style="{ transform: isCollapsed ? 'rotate(180deg)' : 'rotate(0)' }" class="rotate-arrow"/>
                </button>
            </div>
    </div>
    </template>
    
    <script >
    
    export default {
      data() {
        return {
          isCollapsed: false
        }
      },
      methods: {
        sidebarColapse() {
          this.isCollapsed = !this.isCollapsed;
        }
      },
      mounted(){
        /*Código para aplicar o actvie na sidebar*/ 
        const currentRoute = this.$route.path;
        let navRoutes = document.getElementsByClassName("nav-route");
        let navContainers = document.getElementsByClassName("nav-container");
        for(let i = 0; i < navRoutes.length; i++){
            if(navRoutes[i].getAttribute('href') === currentRoute){
                navContainers[i].classList.add('active');
                navContainers[i].classList.remove('text-dark-emphasis');
            };
        };
      },
    }
    </script>
    
    <style scoped>
    .offcanvas{
        border: none;
        width: 200px;
        height: 95vh;  
        top: 5%;
        padding-top: 10%;
    }
    .offcanvas-body{
        bottom: 0;
        margin-right: 0px;
        padding-right: 0px;
        margin-bottom: -200px;
    }
    .nav{   
        margin: 0;
        position: sticky;
        display: flex;
        transition: width 0.6s ease-in-out;
    }
    .list-group-item{
        display: inline-block;
        font-size: 13px;
        margin-left: 7px;
        padding-top: 8px;
        text-decoration: none;
        transition: opacity 0.9s ease-in-out;
    }
    .collapsed {
      width: 50px; 
    }
    
    .colapse-btn{
        padding: 0;
        width: 200px;
        bottom: 0;
        height: 55px;
        transition: width 0.6s ease-in-out;
    }
    .collapsed .colapse-btn{
        width: 50px;
        height: 55px;
    }
    .collapsed .list-group-item{
        visibility: hidden;
        opacity: 0;
    }
    .collapsed .item-bg{
        width: 35px;
        height: 50px;
    }
    .rotate-arrow{
        transition: transform 0.6s ease-in-out;
    }
    .list-group-flush{
        margin-left: -20px;
    }
    .item-bg{
        overflow: hidden;
        transition: width 0.32s, height 0.6s ease-in-out;
        margin-top: 15px;
        padding-left: 5px;
        height: 52px;
        width: 180px;
    }
    .active{
        color: white;
        background: #0B3B69;
        border-radius: 9px;
    }
    .item-bg:hover{
        background: #D9D9D9;
        color: #333333;
        border-radius: 9px;
    }
    </style>