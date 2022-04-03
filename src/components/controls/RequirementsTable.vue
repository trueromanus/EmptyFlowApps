<template>
    <table class="requirements-table">
        <tr>
            <td>
                Processor
            </td>
            <td>
                {{ requirements.processor }}
            </td>
        </tr>
        <tr>
            <td>
                Processor frequency
            </td>
            <td>
                {{ requirements.processorFrenquency }}
            </td>
        </tr>
        <tr>
            <td>
                Memory
            </td>
            <td>
                {{ requirements.ramSpace }}
            </td>
        </tr>
        <tr>
            <td>
                Disk space
            </td>
            <td>
                {{ requirements.hardDriveSpace }}
            </td>
        </tr>
    </table>
</template>

<script>
export default {
    name: `RequirementsTable`,
    props: {
        requirements: {
            type: Object,
            required: true
        }
    }
}
</script>

<style>
.requirements-table {
    width: 90%;    
    border-collapse: collapse;
    border: 1px solid black;
}
.requirements-table tr td {
    border: 1px solid black;
}
.requirements-table td {
    width: 50%;
}

</style>