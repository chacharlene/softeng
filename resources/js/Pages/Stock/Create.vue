<template>
    <div>
        <Layout>
            <div class="flex justify-center w-full">
                <div class="bg-white flex flex-col w-1/3 mt-20 p-6">
                    <h2 class="text-lg">Stock Category Form</h2>
                    <form
                        id="stock-form"
                        name="stock-form"
                        v-on:submit.prevent="submit"
                    >
                        <div class="flex flex-col pt-6">
                            <label for="id">ID</label>
                            <input
                                type="text"
                                id="id"
                                name="id"
                                v-model="form.id"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.id }}
                            </div>
                            {{ form.id }}
                        </div>

                                                <div class="flex flex-col pt-6">
                            <label for="sti">Stock Category ID</label>
                            <input
                                type="text"
                                id="sti"
                                name="sti"
                                v-model="form.sti"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.sti }}
                            </div>
                            {{ form.sti }}
                        </div>


                        <div class="flex flex-col pt-6">
                            <label for="description">Description</label>
                            <input
                                type="text"
                                id="description"
                                name="description"
                                v-model="form.description"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.description }}
                            </div>
                             {{ form.description }}
                        </div>

<div class="flex flex-col pt-6">
                            <label for="oum">OUM</label>
                            <select name="oum" id="oum" v-model="form.oum">
                                <option value="F">PR</option>
                                <option value="R">CRD</option>
                                <option value="R">GAL</option>
                                <option value="R">SGL</option>
                                <option value="R">DZ</option>
                                <option value="R">LOT</option>
                                <option value="R">CTN</option>
                                <option value="R">PK50</option>
                                <option value="R">MM</option>

                            </select>

                            <div class="text-red-700 text-sm">
                                {{ errors.oum }}
                            </div>
                        </div>

                <div class="flex flex-col pt-6">
                            <label for="barcode">Barcode</label>
                            <input
                                type="text"
                                id="barcode"
                                name="barcode"
                                v-model="form.barcode"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.barcode }}
                            </div>
                             {{ form.barcode }}
                        </div>


                        <div class="w-full flex flex-col pt-6">
                            <label for="discontinued">Discontinued</label>
<input type="checkbox" id="discontinued" value="Yes" v-model="form.yesdiscontinued">
<label for="Yes">Yes</label>
<input type="checkbox" id="discontinued" value="No" v-model="form.nodiscontinuedsd">
<label for="No">No</label>




                            <div class="text-red-700 text-sm">
                                {{ errors.discontinued }}
                            </div>
                        </div>

                        <div class="flex flex-col pt-6">
                            <label for="photo">Photo Path</label>
                            <input
                                type="text"
                                id="Photo"
                                name="Photo"
                                v-model="form.photo"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.photo }}
                            </div>
                        </div>

                        <div class="flex flex-col pt-6">
                            <label for="Created">Date Created</label>
                            <input
                                type="text"
                                id="Created"
                                name="Created"
                                v-model="form.Created"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.Created }}
                            </div>
                        </div>


                                                <div class="flex flex-col pt-6">
                            <label for="Updated">Date Updated</label>
                            <input
                                type="text"
                                id="Updated"
                                name="Updated"
                                v-model="form.Updated"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.Updated }}
                            </div>
                        </div>

                        <div class="flex flex-col pt-6">
                            <button
                                type="submit"
                                class="bg-indigo-800 text-white p-2"
                            >
                                Save
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        </Layout>
    </div>
</template>

<script>
import { ref, reactive } from "vue";
import Layout from "@/Layouts/Authenticated";
import { Inertia } from "@inertiajs/inertia";
export default {
    components: {
        Layout,
    },
    props: {
        errors: Object,
    },
    setup(props, context) {




        const form = reactive({
            id: null,
            description: null,
            type: "F",
            stock_account: null,
        });
        const submit = () => {
            Inertia.post(route("stocks.store"), form, {
                onSuccess: () => {
                    // Handle success event
                    form.id = null;
                    form.sti = null;
                    form.description = null;
                    form.oum = "F";
                    form.barcode = null;
                    form.yesdiscontinued = "No";
                    form.nodiscontinued = "Yes";
                    form.photo_path = null;
                    form.Created = null;
                    form.Updated = null;
                    //   this.reset();
                },
            });
        };
        return {
            form,
            submit,
        };


    },
};
</script>
