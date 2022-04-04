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
                Processor bitness
            </td>
            <td>
                {{ requirements.processorBitness }}
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
        <tr>
            <td>
                DirectX
            </td>
            <td>
                {{ requirements.directX }}
            </td>
        </tr>
        <tr>
            <td>
                OpenGL
            </td>
            <td>
                {{ requirements.openGL }}
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
    border: 1px solid lightgray;
    font-family: 'Open Sans', sans-serif;
}
.requirements-table td {
    padding: 8px;
    border-bottom: 1px solid lightgray;
}
.requirements-table td {
    width: 50%;
}

</style>