<script>
import { RouterView } from "vue-router";
import { defineComponent } from "vue";
import AppHeader from "./components/AppHeader.vue";
import AppFooter from "./components/AppFooter.vue";
import ContactModal from "./components/ContactModal.vue";
import { useNavigationStore } from "./stores/navigation";

export default defineComponent({
	name: "App",
	components: {
		AppHeader,
		AppFooter,
		RouterView,
		ContactModal,
	},
	setup() {
		const navigationState = useNavigationStore();

		return {
			navigationState,
		};
	},
});
</script>

<template>
	<AppHeader :class="navigationState.navigationIsOpen ? 'nav-open' : ''" />

	<RouterView />

	<AppFooter />

	<ContactModal />
</template>
