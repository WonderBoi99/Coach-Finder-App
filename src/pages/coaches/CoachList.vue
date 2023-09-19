<template>
    <section>
        Filter
    </section>
    <base-card>
        <section>
            <div class="controls">
                <base-button mode="outline">Refresh</base-button>
                <base-button link="true" to="/register">Register As Coach</base-button>
            </div>
            <ul v-if="hasCoaches">
                <coach-item 
                v-for="coach in filteredCoaches" 
                :key="coach.id" 
                :id="coach.id"
                :firstName="coach.firstName"
                :lastName="coach.lastName"
                :rate="coach.rate"
                :areas="coach.areas"></coach-item>
            </ul>
            <h3 v-else>No coaches found</h3>
        </section>
    </base-card>
</template>

<script>
import CoachItem from '@/components/coaches/CoachItem.vue';
import BaseCard from '@/components/ui/BaseCard.vue';
import BaseButton from '@/components/ui/BaseButton.vue';
import CoachFilter from '@/components/coaches/CoachFilter.vue';

export default {
  components: { CoachItem, BaseCard, BaseButton, CoachFilter },
    computed: {
        filteredCoaches(){
            return this.$store.getters['coaches/coaches'];
        },
        hasCoaches(){
            return this.$store.getters['coaches/hasCoaches'];
        }
    }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>