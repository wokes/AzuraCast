<template>
    <b-tab :title="langTabTitle" active>
        <b-form-group>
            <b-row>
                <b-wrapped-form-group class="col-md-12" id="edit_form_name" :field="form.name">
                    <template #label>
                        <translate key="lang_form_name">Role Name</translate>
                    </template>
                </b-wrapped-form-group>

                <b-wrapped-form-group class="col-md-12" id="edit_form_global_permissions"
                                      :field="form.permissions.global">
                    <template #label>
                        <translate key="lang_form_global_permissions">Global Permissions</translate>
                    </template>
                    <template #description>
                        <translate key="lang_form_global_permissions_desc">Users with this role will have these permissions across the entire installation.</translate>
                    </template>
                    <template #default="props">
                        <b-form-checkbox-group :id="props.id" :options="globalPermissionOptions"
                                               v-model="props.field.$model">
                        </b-form-checkbox-group>
                    </template>
                </b-wrapped-form-group>
            </b-row>
        </b-form-group>
    </b-tab>
</template>

<script>
import BWrappedFormGroup from "~/components/Form/BWrappedFormGroup";
import _ from 'lodash';

export default {
    name: 'AdminPermissionsGlobalForm',
    components: {BWrappedFormGroup},
    props: {
        form: Object,
        globalPermissions: Object
    },
    computed: {
        langTabTitle() {
            return this.$gettext('Global Permissions');
        },
        globalPermissionOptions() {
            return _.map(this.globalPermissions, (permissionName, permissionKey) => {
                return {
                    text: permissionName,
                    value: permissionKey
                };
            });
        },
    }
};
</script>
