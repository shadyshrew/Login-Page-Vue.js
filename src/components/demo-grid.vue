<template>
    <div>
        <table  class="table table-hover table-dark table-bordered table-md">
            <thead>
            <tr>
                <th scope="col" v-on:click="sortDataTable(['ticket'], r1);s1();">
                    Ticket{{searchq}}
                    <i v-if="f1 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r1==true && f1 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r1==false && f1 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['RequestorSeniority'], r2);s2();">
                    RequestorSeniority
                    <i v-if="f2 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r2==true && f2 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r2==false && f2 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['Requestor'], r3);s3();">
                    Requestor
                    <i v-if="f3 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r3==true && f3 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r3==false && f3 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['ITOwner'], r4);s4();">
                    ITOwner
                    <i v-if="f4 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r4==true && f4 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r4==false && f4 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['FiledAgainst'], r5);s5();">
                    FiledAgainst
                    <i v-if="f5 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r5==true && f5 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r5==false && f5 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['TicketType'], r6);s6();">
                    TicketType
                    <i v-if="f6 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r6==true && f6 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r6==false && f6 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['Severity'], r7);s7();">
                    Severity
                    <i v-if="f7 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r7==true && f7 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r7==false && f7 == false" class="fa fa-sort-desc col-1"></i></th>
                <th scope="col" v-on:click="sortDataTable(['Priority'], r8);s8();">
                    Priority
                    <i v-if="f8 == true" class="fa fa-sort col-1"></i>
                    <i v-if="r8==true && f8 == false" class="fa fa-sort-asc col-1"></i>
                    <i v-if="r8==false && f8 == false" class="fa fa-sort-desc col-1"></i></th>
            </tr>
            </thead>
            <tbody>
            <tr  v-for="(t,index) in ticketData" v-if="index < ind" v-on:click="currentt(t)">
                <td>{{t.ticket}}</td>
                <td>{{t.RequestorSeniority}}</td>
                <td>{{t.Requestor}}</td>
                <td>{{t.ITOwner}}</td>
                <td>{{t.FiledAgainst}}</td>
                <td>{{t.TicketType}}</td>
                <td>{{t.Severity}}</td>
                <td>{{t.Priority}}</td>
            </tr>
            </tbody>
        </table>
        <myModal v-if="showModal" @close="showModal = false">
            <h3 slot="header">You've Clicked Ticket {{to.ticket}}</h3>
            <div slot="body">
                Ticket: {{to.ticket}}<br>Requestor: {{to.Requestor}}<br>
                Requestor Seniority: {{to.RequestorSeniority}}<br> ITOwner: {{to.ITOwner}}<br>
                FiledAgainst: {{to.FiledAgainst}}<br> TicketType: {{to.TicketType}}<br>
                Severity: {{to.Severity}}<br> Priority: {{to.Priority}}<br>
                daysOpen: {{to.daysOpen}}<br> Satisfaction: {{to.Satisfaction}}<br>

            </div>
        </myModal>

    </div>
</template>

<script>
    import tickets from '../assets/Sample Data.json'
    import myModal from './myModal.vue'
    export default {
        name: "pageTables",
        props:["searchq"],
        components: {
            myModal
        },
        data() {
            return {
                showModal: false,
                to: null,
                ticketData : tickets,
                ind: 14,
                r1: true,
                r2: true,
                r3: true,
                r4: true,
                r5: true,
                r6: true,
                r7: true,
                r8: true,
                f1: true,
                f2: true,
                f3: true,
                f4: true,
                f5: true,
                f6: true,
                f7: true,
                f8: true
            }
        },
        methods:{
            currentt(a){
                this.to = a
                this.showModal= true;
            },
            show () {
                this.$modal.show(String(this.t));
            },
            hide () {
                this.$modal.hide(String(this.t));
            },
            s1(){
                this.r1 = !this.r1;
                this.f1 = false;
                this.f2 = true;
                this.f3 = true;
                this.f4 = true;
                this.f5 = true;
                this.f6 = true;
                this.f7 = true;
                this.f8 = true;
            },
            s2(){
                this.r2 = !this.r2;
                this.f2 = false;
                this.f1 = true;
                this.f3 = true;
                this.f4 = true;
                this.f5 = true;
                this.f6 = true;
                this.f7 = true;
                this.f8 = true;
            },
            s3(){
                this.r3 = !this.r3;
                this.f3 = false;
                this.f2 = true;
                this.f1 = true;
                this.f4 = true;
                this.f5 = true;
                this.f6 = true;
                this.f7 = true;
                this.f8 = true;
            },
            s4(){
                this.r4 = !this.r4;
                this.f4 = false;
                this.f2 = true;
                this.f3 = true;
                this.f1 = true;
                this.f5 = true;
                this.f6 = true;
                this.f7 = true;
                this.f8 = true;
            },
            s5(){
                this.r5 = !this.r5;
                this.f5 = false;
                this.f2 = true;
                this.f3 = true;
                this.f4 = true;
                this.f1 = true;
                this.f6 = true;
                this.f7 = true;
                this.f8 = true;
            },
            s6(){
                this.r6 = !this.r6;
                this.f6 = false;
                this.f2 = true;
                this.f3 = true;
                this.f4 = true;
                this.f5 = true;
                this.f1 = true;
                this.f7 = true;
                this.f8 = true;
            },
            s7(){
                this.r7 = !this.r7;
                this.f7 = false;
                this.f2 = true;
                this.f3 = true;
                this.f4 = true;
                this.f5 = true;
                this.f6 = true;
                this.f1 = true;
                this.f8 = true;
            },
            s8(){
                this.r8 = !this.r8;
                this.f8 = false;
                this.f2 = true;
                this.f3 = true;
                this.f4 = true;
                this.f5 = true;
                this.f6 = true;
                this.f7 = true;
                this.f1 = true;
            },
            sortDataTable(arrayColNames, asc) {
                for (let i=0;i<arrayColNames.length;i++) {
                    let columnName = arrayColNames[i];
                    this.ticketData = this.ticketData.sort(function(a,b){
                        if (asc) {
                            return (a[columnName] > b[columnName]) ? 1 : -1;
                        } else {
                            return (a[columnName] < b[columnName]) ? 1 : -1;
                        }
                    });
                }
            }
        }

    }
</script>

<style scoped>
    th:hover{
        cursor: pointer;
    }
    table {
        text-align: center;
    }
</style>