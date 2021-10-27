<template>
  <q-page>
    <div class="row">
      <q-table
        dense
        :rows="posts"
        :columns="columns"
        class="col"
        row-key="id"
        separator="cell"
      >
        <template v-slot:body="props">
          <q-tr :props="props">
            <q-td auto-width>
              <q-btn
                size="sm"
                color="accent"
                round
                dense
                @click="props.expand = !props.expand"
                :icon="props.expand ? 'remove' : 'add'"
              />
            </q-td>
            <q-td v-for="col in props.cols" :key="col.name" :props="props">
              {{ col.value }}
            </q-td>
          </q-tr>
          <q-tr v-show="props.expand" :props="props">
            <q-td colspan="100%">
              <div class="text-left">
                {{ props.row.body }}.
              </div>
            </q-td>
          </q-tr>
        </template>
        <!--<template v-slot:body-cell-action="props">
          <q-td :props="props">
            <q-btn
              icon="create"
              color="primary"
              size="sm"
              dense
              class="q-ml-sm"
              @click="editPost(props.row)"
            />
            <q-btn
              icon="delete"
              color="negative"
              size="sm"
              dense
              @click="deletePost(props.row)"
            />
          </q-td>
        </template>-->
      </q-table>
    </div>
  </q-page>
</template>

<script>
/* eslint-disable */
import { defineComponent } from "vue";
import { ref } from "vue";

export default defineComponent({
  name: "PageIndex",
  data() {
    return {
      columns: [
        {
          name: "id",
          label: "Id Post",
          align: "left",
          field: "id",
          sortable: true,
        },
        {
          name: "title",
          label: "Title",
          align: "left",
          field: "title",
          sortable: true,
        },
      ],
      posts: [],
      selected: ref([]),
    };
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    getPosts() {
      this.$axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((res) => {
          this.posts = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    editPost(post) {
      console.log(post);
    },
    deletePost(post) {
      console.log(post);
    },
  },
});
</script>
