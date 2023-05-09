<template>
  <q-layout view="lHr lpR fFf">

    <q-header class="bg-white text-black cabecalho-topo">
      <q-toolbar>
        <q-btn dense flat round @click="alternarDrawerDaEsquerda" />
        <q-toolbar-title class="text-weight-bold titulo-header">
          Página Inicial
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <!-- DRAWER DA ESQUERDA -->
    <q-drawer show-if-above v-model="drawerDaEsquerdaAberto" side="left" bordered :width="405">
      <q-item to="/home" active clickable>
        <q-icon name="fas fa-dove" size="md" color="primary" class="q-pl-xl q-mt-md q-mb-md icone-twitter" />
      </q-item>

      <q-item>
        <q-list padding class="menu-list text-weight-regular q-pr-xl q-mr-md absolute-top-right">
          <q-item to="/home" active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="home" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Página Inicial
            </q-item-section>
          </q-item>

          <q-item to="/home" active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="tag" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Explorar
            </q-item-section>
          </q-item>

          <q-item to="/home" active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="notifications" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Notificações
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="email" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Mensagens
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="bookmark" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Itens Salvos
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="text_snippet" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Listas
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="person" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Perfil
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="fa-regular fa-comment-dots" size="md" color=dark />
            </q-item-section>

            <q-item-section class="texto-drawer-esquerdo">
              Mais
            </q-item-section>
          </q-item>
          <q-btn class="btn-width-fixa" unelevated rounded no-caps color="light-blue" label="Tweetar"
            text-color="white" />
          <div class="q-py-lg flex wrap ">
            <q-avatar size="xl">
              <img src="https://pbs.twimg.com/profile_images/1528093885704052741/j0bYT17V_400x400.jpg">
            </q-avatar>
            <span class="q-pl-sm">
              <strong> {{username}} </strong>
              <br> {{user}}
            </span>
          </div>

        </q-list>

      </q-item>


    </q-drawer>

    <!-- DRAWER DA DIREITA -->
    <q-drawer show-if-above v-model="drawerDaDireitaAberto" side="right" bordered :width="547">
      <q-input placeholder="Buscar no Twitter" class="q-ma-sm q-mb-md input-drawer-direito" rounded outlined dense
        v-model="text">

        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>

      <q-list padding class="lista-drawer-direito">
        <q-item>
          <q-item-section>
            <h6 class="titulo-drawer-direito">O que está acontecendo</h6>
            <q-item-label caption>Brasil ° há 5 minutos</q-item-label>
            <q-item-label class="texto-drawer-direito">Suspeito de participação no desaparecimento de Bruno e Dom é levado
              ao local das buscas
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-item>
          <q-item-section>
            <q-item-label caption>Esportes ° Essa tarde</q-item-label>
            <q-item-label class="texto-drawer-direito">Ricardo Goulart</q-item-label>
          </q-item-section>
        </q-item>

        <q-item>
          <q-item-section>
            <q-item-label caption>Entretenimento ° Assunto do Momento</q-item-label>
            <q-item-label class="texto-drawer-direito">Dakota Johnson</q-item-label>
          </q-item-section>
        </q-item>

        <q-item>
          <q-item-section>
            <q-item-label caption>Guerra na Ucrânia ° AO VIVO</q-item-label>
            <q-item-label class="texto-drawer-direito">Líderes da Otan se reúnem em Bruxelas e devem abordar envio de
              armas à Ucrânia</q-item-label>
          </q-item-section>
        </q-item>

        <q-item>
          <q-item-section>
            <q-item-label caption>Saúde ° Ontem</q-item-label>
            <q-item-label class="texto-drawer-direito">Como se proteger contra a varíola do macaco
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-item>
          <q-item-section>
            <q-item-label caption>Casa Vogue Brasil ° Ontem</q-item-label>
            <q-item-label class="texto-drawer-direito">Ator Marcelo Faria mostra área de lazer de sua casa com vista
              incrível para o mar na Espanha
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-item-label class="q-pl-md texto-drawer-mostrar-mais">Mostrar mais</q-item-label>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const drawerDaEsquerdaAberto = ref(false)
    const drawerDaDireitaAberto = ref(false)

    return {
      drawerDaEsquerdaAberto,
      alternarDrawerDaEsquerda() {
        drawerDaEsquerdaAberto.value = !drawerDaEsquerdaAberto.value
      },

      drawerDaDireitaAberto,
      alternarDrawerDaDireita() {
        drawerDaDireitaAberto.value = !drawerDaDireitaAberto.value
      }
    }
  },
  data() {
    return {
      username: 'Cadu Maverick',
      user: ' @cadumaverick',
    }
  }
}
</script>

<style>
.cabecalho-topo {
  width: 584px;
  height: 50px;
}

.titulo-header {
  position: relative;
  right: 40px;
}

.icone-twitter {
  margin-left: 100px;
}

.texto-drawer-esquerdo {
  color: black;
  font-size: 20px;
  line-height: 2;
}

.input-drawer-direito {
  width: 350px;
  background-color: #f4f4f4;
  border-radius: 20px;
  margin-left: 30px;
}

.lista-drawer-direito {
  width: 350px;
  height: 600px;
  padding-left: 5px;
  margin-left: 30px;
  background-color: #f4f4f4;
  border-radius: 20px;
}

.titulo-drawer-direito {
  font-size: 20px;
  font-weight: bold;
  padding-bottom: 20px;
}

.texto-drawer-direito {
  font-size: 15px;
  font-weight: bold;
  padding-bottom: 8px;
  margin-right: 20px;
}

.texto-drawer-mostrar-mais {
  color: blue;
  cursor: pointer;
  padding-top: 35px;
  width: 100px;
}

.btn-width-fixa {
  margin-top: 20px;
  width: 200px;
  padding: 10px 0;
}
</style>