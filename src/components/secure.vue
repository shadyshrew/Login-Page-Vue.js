<template>
    <div id="secure">

        <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
            <a class="navbar-brand" href="https://www.npinnovations.com/"><img src="../assets/np-logo.png" alt="logo" height="30" width="30"></a>
            <ul class="navbar-nav">
                <li id = "whiteit" class="nav-item navbar-dark">
                    Secure Area
                </li>
            </ul>
            <ul id = "" class = "nav navbar-nav ml-auto"><button class="btn btn-primary btn-danger btn-lg "  v-on:click="logout()">
                Logout
                <i class="fa fa-sign-out"></i>
            </button> </ul>
        </nav>
        <div class="row">
            <div class="small col">
                <pieChart :data = "seniority"/>
            </div>
            <div class="smaller col">
                <pieChart :data = "filed"/>
            </div>
            <div class="small col">
                <pieChart :data = "tickettype"/>
            </div>
            <div class="smaller col">
                <pieChart :data = "severity"/>
            </div>
            <div class="smaller col">
                <pieChart :data = "satisfaction"/>
            </div>
        </div>
            <pageTables/>


    </div>
</template>

<script>
    import pageTables from './pageTables.vue'
    import pieChart from './pieChart.vue'
    import tickets from '../assets/Sample Data.json'
    import myModal from './myModal.vue'
    export default {
        name: "Secure",
        components: {
            pageTables,
            pieChart,
            myModal
        },
        data () {
            return {
                myTicks: tickets,
                seniority: {
                    labels: ['Junior', 'Regular', 'Senior', 'Management'],
                    datasets: [
                        {
                            label: 'Requestor Seniority',
                            backgroundColor: ['#003f5c','#7a5195','#ef5675','#ff6110'],
                            data: [40, 20, 12, 390]
                        }
                    ]
                },
                filed: {
                    labels: ['Systems', 'Software', 'Access/Login', 'Hardware'],
                    datasets: [
                        {
                            label: 'Filed Against',
                            backgroundColor: ['#00876c','#80b36a','#ebd877','#eb8e4d'],
                            data: [40, 20, 12, 390]
                        }
                    ]
                },
                tickettype: {
                    labels: ['Systems', 'Software', 'Access/Login', 'Hardware'],
                    datasets: [
                        {
                            label: 'Filed Against',
                            backgroundColor: ['#00876c','#80b36a','#ebd877','#eb8e4d'],
                            data: [40, 20, 12, 390]
                        }
                    ]
                },
                severity: {
                    labels: ['Systems', 'Software', 'Access/Login', 'Hardware'],
                    datasets: [
                        {
                            label: 'Filed Against',
                            backgroundColor: ['#00876c','#80b36a','#ebd877','#eb8e4d'],
                            data: [40, 20, 12, 390]
                        }
                    ]
                },
                satisfaction: {
                    labels: ['Systems', 'Software', 'Access/Login', 'Hardware'],
                    datasets: [
                        {
                            label: 'Filed Against',
                            backgroundColor: ['#00876c','#80b36a','#ebd877','#eb8e4d'],
                            data: [40, 20, 12, 390]
                        }
                    ]
                }

            }
        },
        mounted () {

        },
        methods: {
            logout() {
                this.$emit("authenticated", false);
            }

        }

    }
</script>

<style scoped>
    pieChart{
        padding-top: 100px;
    }
    #secure {
        background-color: transparent;
        padding: 0px;
        margin-top: 0px;
    }
    #logout{
        background-color: transparent;
    }

    .small {
        max-width: 20%;
        max-height: 20%;
        padding-bottom: 60px;}


    button{
        background: transparent;
        border: 0px;
    }
    i {
        padding-right: 20px;
        color: white;
    }
    .smaller {
        max-width: 20%;
        max-height: 20%;
        padding-bottom: 60px;
    }

    #whiteit {
        color: white;
    }
</style>