<script>
import EmailIcon from "@components/icons/IconEmail.vue";
import { useNavigationStore } from "@/stores/navigation";

export default {
	name: "ContactModal",
	components: {
		EmailIcon,
	},
	data() {
		return {
			navigationState: {},
			userRole: [
				"interessierte Person",
				"Unternehmen",
				"Verein",
				"NGO",
				"willy nilly",
			],
		};
	},
	mounted() {
		this.navigationState = useNavigationStore();
	},
};
</script>

<template>
	<div
		id="contact-modal"
		tabindex="-1"
		aria-hidden="true"
		class="fixed top-0 left-0 right-0 z-[100] w-full p-4 hidden overflow-x-hidden overflow-y-auto md:inset-0 h-modal md:h-full"
	>
		<div class="relative w-full h-auto max-w-screen-sm">
			<!-- Modal content -->
			<div class="relative bg-snow text-coal rounded-xl shadow-2xl">
				<!-- Modal header -->
				<div class="flex items-start justify-between p-5 rounded-t">
					<h3>Kontakt</h3>

					<button
						@click="navigationState.closeModal"
						type="button"
						class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center"
					>
						<svg
							class="w-5 h-5"
							fill="currentColor"
							viewBox="0 0 20 20"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								fill-rule="evenodd"
								d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
								clip-rule="evenodd"
							></path>
						</svg>
					</button>
				</div>
				<!-- Modal body -->
				<div class="p-6 pt-0 space-y-6 md:pt-0 md:mt-0 text-coal">
					<p class="text-base hidden">
						Beschreibe uns dein Anliegen und wir kontaktieren dich.
					</p>

					<p class="text-base !m-0">
						Schön dass du dich für uns interessierst. Wir freuen uns
						über deine Nachricht. Wie du siehst arbeiten wir noch an
						dieser Seite. Wenn du uns kontaktieren möchtest, schreib
						uns doch eine E-Mail an
						<a
							href="mailto:hey@remorrow.world"
							class="text-rich-electric-blue hover:text-blue-600"
							>hey@remorrow.world</a
						>
					</p>
					<form
						name="user-contact"
						method="POST"
						data-netlify="true"
						data-netlify-honeypot="bot-field"
						class="flex flex-col gap-5 hidden"
					>
						<input
							type="hidden"
							name="form-name"
							value="user-contact"
						/>
						<!-- User Message -->
						<div>
							<label
								for="message"
								class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
								>Deine Nachricht:</label
							>
							<textarea
								id="message"
								rows="4"
								class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-200 shadow-inner focus:border-rich-electric-blue"
								placeholder="Was brauchst du? Was möchtest du erreichen? Wieso glaubst du wir können dir helfen?"
							></textarea>
						</div>

						<!-- Select Purpose -->
						<div>
							<label
								for="user-role"
								class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
								>Ich melde mich als:</label
							>
							<select
								id="user-role"
								name="role[]"
								multiple
								class="bg-gray-50 border-gray-200 shadow-inner text-gray-900 text-sm rounded-lg block w-full p-2.5 focus:border-rich-electric-blue"
							>
								<option value="role">
									interessierte Person
								</option>
								<option value="company">Unternehmen</option>
								<option value="association">Verein</option>
								<option value="ngo">NGO</option>
								<option value="willy-nilly">willy nilly</option>
							</select>
						</div>

						<!-- User E-mail -->
						<div>
							<label
								for="email"
								class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
								>Deine E-Mail Adresse:</label
							>
							<div class="flex">
								<span
									class="inline-flex items-center px-3 text-sm text-snow bg-coal rounded-l-md"
								>
									<EmailIcon class="fill-current h-4" />
								</span>

								<input
									type="email"
									id="email"
									class="rounded-none rounded-r-lg border-gray-200 bg-white text-coal focus:ring-rich-electric-blue focus:border-rich-electric-blue block flex-1 min-w-0 w-full text-sm p-2.5"
									placeholder="maja.göpel@me.com"
								/>
							</div>
						</div>

						<!-- Modal footer -->
						<div
							class="flex items-center py-6 space-x-2 border-t rounded-b justify-between"
						>
							<button
								type="submit"
								class="flex-1 text-snow bg-rich-electric-blue hover:bg-coal hover:text-rich-electric-blue focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
							>
								Abschicken
							</button>
							<button
								type="button"
								class="modal-close flex-1 text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-blue-300 rounded-lg text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10"
							>
								Abbrechen
							</button>
						</div>
					</form>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped></style>
