<template>
	<div>
		<div class="margines">
			<h4>Jak kolorować prostokąt</h4>
			<h5><ol>
			<li>Wybierz bok prostokąta do kolorowania</li>
			<li>Potwierdź przyciskiem "chcę kolorować prostokąt"</li>
			<li>Wpisz liczbę "1" w miejsca, gdzie prostokąt ma być pomalowany</li>
			<li>Potwierdź klikając "Koloruj!"</li></ol></h5>
		</div>

		
		
		<div v-if="sqrs==false">
			<input type="text" v-model="num" placeholder="długość boku(max 4)">
			<button v-on:click="squares()" class="btn btn-success">Chcę pokolorować prostokąt</button> 
		</div>
		<div v-if="sqrsrd==false">
			<div v-for="ind in indexes" v-bind:key="ind">
				<div class="row">
					<div class="col-2 col-md-1" v-for="ind2 in indexes" v-bind:key="ind2">
						<input class="squa" type="text" v-model="tab[ind2+num*ind]">
					</div>
				</div>
			</div>
			<button v-on:click="donesqrs()" class="btn btn-success margines">Koloruj!</button>
		</div>
		<div v-if="sqrsrd==true" class="sqrs2">
			<div v-for="ind in indexes" v-bind:key="ind">
				<div class="row">
					<div v-for="ind2 in indexes" v-bind:key="ind2">
						<div class="col-1 squa2 coloredfloat" v-if="tab[ind2+num*ind]==1"></div>
						<div class="col-1 squa2" v-else></div>
					</div>
				</div>
			</div>
			<button class="btn btn-danger margin-top" v-on:click="back()">Powrót</button>
		</div>
		
	</div>
</template>
<script>
export default{
	data:function(){
	return{
		indexes:[],
		tab:[],
		num:null,
		sqrs:false,
		sqrsrd:null,
	
	}
	},
	methods:{
	squares:function(){
		if(this.num<=4){
		this.sqrs=true;
		this.sqrsrd=false;
		for(var a=0;a<this.num;a++){
		this.indexes.push(a);
		}
		}
	},
	donesqrs:function(){
		this.sqrsrd=true;
	},
	back:function(){
		this.sqrsrd=false;
	}
	
	
	},


}
</script>
<style>
	.squa{
	width:100%;
	height:70%;
	margin:20px;
	}
	.coloredfloat{
	width:100%;
	height:auto;
	background-color:black;
	}
	.sqrs2{
	margin-left:50px;
	}
	.squa2{
	width:100%;
	margin:0px;
	height:2rem;
	}
	.margin{
	margin:2rem;
	}
	.margin-top{
	margin-top:2rem;
	}
	
</style>
