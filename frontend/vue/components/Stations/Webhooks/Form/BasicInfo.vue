<template>
    <b-tab :title="langTabTitle" active>
        <b-form-group>
            <b-row>
                <b-wrapped-form-group class="col-md-12" id="form_edit_name" :field="form.name">
                    <template #label>
                        <translate key="lang_form_edit_name">Web Hook Name</translate>
                    </template>
                    <template #description>
                        <translate key="lang_form_edit_name_desc">Choose a name for this webhook that will help you distinguish it from others. This will only be shown on the administration page.</translate>
                    </template>
                </b-wrapped-form-group>

                <b-wrapped-form-group v-if="triggerOptions.length > 0" class="col-md-12"
                                      id="edit_form_triggers"
                                      :field="form.triggers">
                    <template #label>
                        <translate key="lang_form_triggers">Web Hook Triggers</translate>
                    </template>
                    <template #description>
                        <translate key="lang_form_triggers_desc">This web hook will only run when the selected event(s) occur on this specific station.</translate>
                    </template>
                    <template #default="props">
                        <b-form-checkbox-group :id="props.id" :options="triggerOptions"
                                               v-model="props.field.$model" stacked>
                        </b-form-checkbox-group>
                    </template>
                </b-wrapped-form-group>
            </b-row>
        </b-form-group>
    </b-tab>
</template>

<script>
import BWrappedFormGroup from "~/components/Form/BWrappedFormGroup";

export default {
    name: 'BasicInfo',
    components: {BWrappedFormGroup},
    props: {
        form: Object,
        triggerOptions: Array
    },
    computed: {
        langTabTitle() {
            return this.$gettext('Basic Info');
        }
    }
}
</script>
