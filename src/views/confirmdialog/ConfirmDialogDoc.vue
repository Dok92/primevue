<template>
	<div class="content-section documentation">
		<TabView>
			<TabPanel header="Documentation">
                <h5>Mitt EventBus</h5>
                <p>ConfirmDialog requires <a href="https://www.npmjs.com/package/mitt">Mitt</a>, a tiny 200b EventBus implementation.</p>
<pre v-code>
<code>
npm install mitt --save

</code></pre>

                <h5>ConfirmationService</h5>
                <p>ConfirmDialog is controlled via the <i>ConfirmationService</i> that needs to be installed globally before the application
                    instance is created.</p>
<pre v-code.script>
<code>
import {createApp} from 'vue';
import ConfirmationService from 'primevue/confirmationservice';

const app = createApp(App);
app.use(ConfirmationService);

</code></pre>

				<h5>Import</h5>
<pre v-code.script>
<code>
import ConfirmDialog from 'primevue/confirmdialog';

</code></pre>

				<h5>Getting Started</h5>
				<p>ConfirmDialog is displayed by calling the <i>require</i> method of the <i>$confirm</i> instance by passing the options to customize the Dialog. Suggested location of the Dialog is the main application component
                where it can be shared by any component within the application.</p>
<pre v-code>
<code>
&lt;ConfirmDialog&gt;&lt;/ConfirmDialog&gt;

&lt;Button @click="delete()" icon="pi pi-check" label="Confirm"&gt;&lt;/Button&gt;
</code></pre>

<pre v-code.script>
<code>
export default {
	methods: {
        delete() {
            this.$confirm.require({
                message: 'Are you sure you want to proceed?',
                header: 'Confirmation',
                icon: 'pi pi-exclamation-triangle',
                accept: () => {
                    //callback to execute when user confirms the action
                },
                reject: () => {
                    //callback to execute when user rejects the action
                }
            });
        },
    }
}

</code></pre>

                <h5>Composition API</h5>
                <p>The service can be injected with the <i>useConfirm</i> function.</p>
<pre v-code.script>
<code>
import { defineComponent } from "vue";
import { useConfirm } from "primevue/useconfirm";

export default defineComponent({
    setup() {
        const confirm = useConfirm();
        confirm.require({
            message: 'Are you sure you want to proceed?',
            header: 'Confirmation',
            icon: 'pi pi-exclamation-triangle',
            accept: () => {
                //callback to execute when user confirms the action
            },
            reject: () => {
                //callback to execute when user rejects the action
            }
        });
    }
})

</code></pre>

                <h5>Close Confirmation</h5>
                <p>The dialog can also be hidden programmatically using the <i>close</i> method.</p>
<pre v-code.script>
<code>
export default {
	methods: {
        discard() {
            this.$confirm.close();
        }
    }
}

</code></pre>

                <h5>Confirmation Options</h5>
                <p>ConfirmDialog can be customized with various options listed here.</p>
                <div class="doc-tablewrapper">
                    <table class="doc-table">
                        <thead>
                            <tr>
                                <th>Name</th>
                                <th>Type</th>
                                <th>Default</th>
                                <th>Description</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>message</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Message of the confirmation.</td>
                            </tr>
                            <tr>
                                <td>group</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Optional key to match the key of the confirmation, useful to target a specific confirm dialog instance.</td>
                            </tr>
                            <tr>
                                <td>icon</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Icon to display next to the message.</td>
                            </tr>
                            <tr>
                                <td>header</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Header text of the dialog.</td>
                            </tr>
                            <tr>
                                <td>accept</td>
                                <td>Function</td>
                                <td>null</td>
                                <td>Callback to execute when action is confirmed.</td>
                            </tr>
                            <tr>
                                <td>reject</td>
                                <td>Function</td>
                                <td>null</td>
                                <td>Callback to execute when action is rejected.</td>
                            </tr>
                            <tr>
                                <td>acceptLabel</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Label of the accept button.</td>
                            </tr>
                            <tr>
                                <td>rejectLabel</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Label of the reject button.</td>
                            </tr>
                            <tr>
                                <td>acceptIcon</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Icon of the accept button.</td>
                            </tr>
                            <tr>
                                <td>rejectIcon</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Icon of the reject button.</td>
                            </tr>
                            <tr>
                                <td>acceptClass</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Style class of the accept button.</td>
                            </tr>
                            <tr>
                                <td>rejectClass</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Style class of the reject button.</td>
                            </tr>
                            <tr>
                                <td>blockScroll</td>
                                <td>boolean</td>
                                <td>true</td>
                                <td>Whether background scroll should be blocked when dialog is visible.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

				<h5>Properties</h5>
				<div class="doc-tablewrapper">
					<table class="doc-table">
						<thead>
                            <tr>
                                <th>Name</th>
                                <th>Type</th>
                                <th>Default</th>
                                <th>Description</th>
                            </tr>
						</thead>
						<tbody>
                            <tr>
                                <td>group</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Optional key to match the key of the confirmation, useful to target a specific confirm dialog instance.</td>
                            </tr>
						</tbody>
					</table>
				</div>

				<h5>Styling</h5>
				<p>ConfirmDialog inherits all the classes from the Dialog component, visit <router-link to="/dialog">dialog</router-link> for more information.</p>
				<div class="doc-tablewrapper">
					<table class="doc-table">
						<thead>
						<tr>
							<th>Name</th>
							<th>Element</th>
						</tr>
						</thead>
						<tbody>
                            <tr>
                                <td>p-confirm-dialog</td>
                                <td>Container element.</td>
                            </tr>
						</tbody>
					</table>
				</div>

				<h5>Dependencies</h5>
				<p>Mitt.</p>
			</TabPanel>

			<TabPanel header="Source">
				<a href="https://github.com/primefaces/primevue/tree/master/src/views/dialog" class="btn-viewsource" target="_blank" rel="noopener noreferrer">
					<span>View on GitHub</span>
				</a>
<pre v-code>
<code><template v-pre>
&lt;ConfirmDialog&gt;&lt;/ConfirmDialog&gt;
&lt;ConfirmDialog group="positionDialog"&gt;&lt;/ConfirmDialog&gt;

&lt;div class="card"&gt;
    &lt;h5&gt;Basic&lt;/h5&gt;
    &lt;Button @click="confirm1()" icon="pi pi-check" label="Confirm" class="p-mr-2"&gt;&lt;/Button&gt;
    &lt;Button @click="confirm2()" icon="pi pi-times" label="Delete"&gt;&lt;/Button&gt;

    &lt;h5&gt;Position&lt;/h5&gt;
    &lt;div class="p-grid p-dir-col"&gt;
        &lt;div class="p-col"&gt;
            &lt;Button @click="confirmPosition('left')" icon="pi pi-arrow-right" label="Left" class="p-button-help p-mr-2"&gt;&lt;/Button&gt;
            &lt;Button @click="confirmPosition('right')" icon="pi pi-arrow-left" label="Right" class="p-button-help"&gt;&lt;/Button&gt;
        &lt;/div&gt;
        &lt;div class="p-col"&gt;
            &lt;Button @click="confirmPosition('topleft')" icon="pi pi-arrow-down" label="TopLeft" class="p-button-warning p-mr-2"&gt;&lt;/Button&gt;
            &lt;Button @click="confirmPosition('top')" icon="pi pi-arrow-down" label="Top" class="p-button-warning p-mr-2"&gt;&lt;/Button&gt;
            &lt;Button @click="confirmPosition('topright')" icon="pi pi-arrow-down" label="TopRight" class="p-button-warning"&gt;&lt;/Button&gt;
        &lt;/div&gt;
        &lt;div class="p-col"&gt;
            &lt;Button @click="confirmPosition('bottomleft')" icon="pi pi-arrow-up" label="BottomLeft" class="p-button-success p-mr-2"&gt;&lt;/Button&gt;
            &lt;Button @click="confirmPosition('bottom')" icon="pi pi-arrow-up" label="Bottom" class="p-button-success p-mr-2"&gt;&lt;/Button&gt;
            &lt;Button @click="confirmPosition('bottomright')" icon="pi pi-arrow-up" label="BottomRight" class="p-button-success"&gt;&lt;/Button&gt;
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;
</template>
</code></pre>

<pre v-code.script>
<code>
export default {
    methods: {
        confirm1() {
            this.$confirm.require({
                message: 'Are you sure you want to proceed?',
                header: 'Confirmation',
                icon: 'pi pi-exclamation-triangle',
                accept: () => {
                    this.$toast.add({severity:'info', summary:'Confirmed', detail:'You have accepted', life: 3000});
                },
                reject: () => {
                    this.$toast.add({severity:'info', summary:'Rejected', detail:'You have rejected', life: 3000});
                }
            });
        },
        confirm2() {
            this.$confirm.require({
                message: 'Do you want to delete this record?',
                header: 'Delete Confirmation',
                icon: 'pi pi-info-circle',
                acceptClass: 'p-button-danger',
                accept: () => {
                    this.$toast.add({severity:'info', summary:'Confirmed', detail:'Record deleted', life: 3000});
                },
                reject: () => {
                    this.$toast.add({severity:'info', summary:'Rejected', detail:'You have rejected', life: 3000});
                }
            });
        },
        confirmPosition(position) {
            this.$confirm.require({
                key: 'positionDialog',
                message: 'Do you want to delete this record?',
                header: 'Delete Confirmation',
                icon: 'pi pi-info-circle',
                position: position,
                accept: () => {
                    this.$toast.add({severity:'info', summary:'Confirmed', detail:'Record deleted', life: 3000});
                },
                reject: () => {
                    this.$toast.add({severity:'info', summary:'Rejected', detail:'You have rejected', life: 3000});
                }
            });
        }
    }
}

</code></pre>
			</TabPanel>
		</TabView>
	</div>
</template>