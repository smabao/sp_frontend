<template>
  <q-layout view="hHh lpR fFf">
    <q-page-container>
        <q-page class="flex flex-center text-center">
          <div class="q-gutter-sm flex text-center">
            <div style="width: 100%; height: 50%;">
              <h2> Job Order Requests </h2>
              <q-input borderless dense debounce="300" v-model="filter" placeholder="Search">
                <template v-slot:append>
                  <q-icon name="search" />
                </template>
              </q-input>
              <q-table
                class="my-sticky-column-table"
                :data="data"
                :columns="columns"
                hide-bottom
                row-key="id"
                :filter="filter"
            />
            </div>
          </div>
        </q-page>
        <router-view/>
    </q-page-container>
  </q-layout>
</template>

<style lang="sass">

  td:first-child
    background-color: #e8a87c

  th:first-child,
  td:first-child
    position: sticky
    left: 0
    z-index: 1
</style>

<script>
export default {
  data () {
    return {
      filter: '',
      columns: [
        {
          id: 'Job Order Number',
          required: true,
          label: 'Job Order Number',
          align: 'left',
          field: row => row.id,
          format: val => `${val}`,
          sortable: true
        },
        {
          name: 'name',
          align: 'center',
          label: 'Name',
          field: 'name',
          sortable: true
        },
        {
          name: 'unit',
          align: 'center',
          label: 'Unit',
          field: 'unit',
          sortable: true
        },
        {
          name: 'location',
          align: 'center',
          label: 'Location',
          field: 'location',
          sortable: true
        },
        {
          name: 'date',
          align: 'center',
          label: 'Date Filed',
          field: 'date',
          sortable: true
        }
      ],
      data: [
        {
          id: 1,
          name: 'Construction',
          unit: 'DPSM',
          location: 'Miagao',
          date: '2018/12/01'
        },
        {
          id: 2,
          name: 'Construction',
          unit: 'Balay Gumamela',
          location: 'Miagao',
          date: '2018/12/01'
        }
      ]
    }
  }
}
</script>
