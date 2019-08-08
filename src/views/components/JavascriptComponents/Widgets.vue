<template>
  <div>
    <small class="d-block text-uppercase font-weight-bold mb-3">Counters</small>
    <div class="row">
      <div
        v-for="(counter, index) in counters"
        :key="index"
        class="col-sm-12 mb-3 col-lg-4">
        <widget
          decimal-separator=","
          :icon="counter.icon"
          :title="counter.title"
          :format="counter.format"
          :hint="counter.hint"
          :to-fixe="counter.toFixe"
          :variant="counter.variant"
          :description="counter.description"
          :value="counter.value"
        >
        </widget>
      </div>
    </div>
  </div>
</template>

<script>
  import Widget from '../../../components/Counter'

  export default {
    name: 'Widgets',
    components: { Widget },
    data(){
      return {
        counters: [
          {
            title: 'Users',
            variant: 'secondary',
            description: 'last hour',
            value: 584,
            toFixe: 0,
            format:'%',
            icon: {
              class: 'ni ni-single-02',
              background: 'danger'
            },
            hint: {
              value: 3.5,
              format:'%',
              toFixe: 2,
              icon: 'fa fa-arrow-up',
              color: 'success'
            }
          },
          {
            title: 'Buket',
            variant: 'success',
            description: 'last hour',
            value: 5584,
            toFixe: 1,
            format:'MB',
            icon: {
              class: 'ni ni-box-2',
              background: 'dark'
            },
            hint: {
              value: 1.1,
              format:'%',
              toFixe: 2,
              icon: 'fa fa-arrow-down',
              color: 'danger',
            }
          },
          {
            title: 'Visits',
            variant: 'default',
            description: 'last hour',
            value: 584,
            format:'%',
            icon: {
              class: 'ni ni-chart-bar-32',
              background: 'dark'
            },
            hint: {
              value: 10,
              format:'%',
              icon: 'fa fa-arrow-down',
              color: 'danger'
            }
          }
        ]
      }
    }
  }
</script>
