<template>
  <q-page class="container" padding>
    <p class="text-h4">Formulário</p>
    <q-form
      class="row q-col-gutter-lg"
      @submit="onSubmit"
      @reset="onReset"
      ref="myForm"
    >
      <q-input
        outlined
        v-model="form.nome"
        color="deep-purple"
        label="Nome"
        class="col-md-12 col-sm-12 col-xs-12"
        :rules="[(val) => (val && val.length > 0) || 'Nome obrigatório.']"
      >
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>
      <q-input
        v-model.number="form.idade"
        type="number"
        outlined
        label="Idade"
        class="col-md-12 col-sm-12 col-xs-12"
        :rules="[
          (val) => (val !== null && val != '') || 'Idade obrigatória.',
          (val) => (val > 0 && val < 100) || 'Coloque uma idade real.',
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>
      <q-input
        outlined
        v-model="form.email"
        type="email"
        suffix="@gmail.com"
        label="E-mail"
        class="col-md-12 col-sm-12 col-xs-12"
        :rules="[(val) => (val && val.length > 0) || 'Email obrigatório.']"
      >
        <template v-slot:prepend>
          <q-icon name="mail" />
        </template>
      </q-input>
      <q-input
        outlined
        v-model="form.telefone"
        label="Telefone"
        mask="(##) ##### - ####"
        class="col-md-12 col-sm-12 col-xs-12"
        unmasked-value
        :rules="[
          (val) => (val && val.length > 0) || 'Telefone obrigatório.',
          (val) => val.length === 11 || 'Coloque um telefone real.',
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="phone" />
        </template>
      </q-input>
      <q-select
        outlined
        v-model="form.tipoPessoa"
        :options="optionsTipoPessoa"
        label="Tipo de Pessoa"
        class="col-md-12 col-sm-12 col-xs-12"
        emit-value
        map-options
        :rules="[
          (val) => (val && val.length > 0) || 'Tipo de Pessoa obrigatório.',
        ]"
      />
      <span class="text-bold">Sexo</span>
      <q-option-group
        v-model="form.sexo"
        :options="optionsSexo"
        label="Sexo"
        color="primary"
        class="col-md-12 col-sm-12 col-xs-12"
      />
      <span class="text-bold">Possui alguma dificuldade?</span>
      <q-option-group
        v-model="form.dificuldades"
        :options="optionsDificuldades"
        type="checkbox"
        class="col-md-12 col-sm-12 col-xs-12"
      />
      <q-toggle
        v-model="form.notificacoes"
        icon="mail"
        label="Receber Notificações"
        class="col-md-12 col-sm-12 col-xs-12"
      />
      <div class="col-12">
        <q-btn
          label="Cadastrar"
          type="submit"
          color="primary"
          class="float-right"
        />
        <q-btn
          label="Limpar"
          type="reset"
          color="default"
          class="float-right text-grey-10 q-mr-md"
          size="lg"
        />
      </div>
    </q-form>
  </q-page>
</template>

<script>
/* eslint-disable */
import { defineComponent } from "vue";

export default defineComponent({
  name: "PageIndex",
  data() {
    return {
      form: {
        nome: "",
        idade: null,
        email: "",
        telefone: "",
        tipoPessoa: "",
        sexo: "NI",
        dificuldades: [],
        notificacoes: false
      },
      optionsTipoPessoa: [
        {
          label: "Pessoa Física",
          value: "pf",
        },
        {
          label: "Pessoa Jurídica",
          value: "pj",
        },
      ],
      optionsSexo: [
        {
          label: "Não Informado",
          value: "NI",
        },
        {
          label: "Masculino",
          value: "M",
        },
        {
          label: "Feminino",
          value: "F",
        },
      ],
      optionsDificuldades: [
        {
          label: "Motoras",
          value: "motoras",
        },
        {
          label: "Visuais",
          value: "visuais",
        },
        {
          label: "Repiratórias",
          value: "respiratorias",
        },
      ],
    };
  },
  methods: {
    onSubmit() {
      this.$q.notify({
        message: "Cadastro realizado com sucesso!",
        color: "positive",
        icon: "check_circle_outline",
      });
      this.onReset();
    },
    async onReset() {
      await this.resetForm();
      this.$refs.myForm.resetValidation();
    },
    async resetForm() {
      this.form = {
        nome: "",
        idade: null,
        email: "",
        telefone: "",
        tipoPessoa: "",
        sexo: "NI",
        dificuldades: [],
        notificacoes: false
      };
    },
  },
});
</script>
