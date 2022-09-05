<template>
    
    <div class="row">
        <div class="column medium-12">
            <div class="test-canvas-controls">
                <label class="mute-error-sound">
                    <input  type="checkbox">
                    <i class="fa fa-fw fa-volume-up"></i> 
                    <span>
                        كتم صوت الخطأ
                    </span>
                </label> 
                <button  class="button secondary small lesson-restart-button">إعادة</button>
                <h5 style="margin:0 2em ;"> مؤقت {{minutes+":"+seconds}}</h5>
            </div>
            <div class="panel radius">
                <div class="test-canvas status-0" style="height: 100px;">
                    <div style="overflow:scroll; height: 100%;">
                       <div v-for="(line,j) of this.inputs" class="line" :key="j">
                        <span v-for="(element,i) of line" :key="i" :class="element[1]" >{{element[0]}}</span>
                       </div>
                    </div>
                  
                </div>
            </div>
          
        </div>
    </div>
        
    
</template>

<script>
import { toNumber } from '@vue/shared';

    export default {
        props:['trainText','timer'],
        data:function(){
            return{
               
                currentIndex:0,
                error_keys:[],
                success_keys:[],
                inputs:[],
                minutes:0,
                seconds:0,
                startcounting:false,
                

            }
        },
       
       methods:{
        countDownTimer () {

                if (this.seconds > 0 || this.minutes>0) {
                    setTimeout(() => {
                        if(this.seconds>0)
                            this.seconds--;
                        else
                            if(this.minutes>0)
                            {
                                this.minutes--;
                                this.seconds=59;
                            }
                     
                        this.countDownTimer()
                    }, 1000)
                }
            }
        ,
        
        updateText(event){
          
           if(!this.startcounting)
           {
            this.countDownTimer ()
            this.startcounting=!this.startcounting
           }


            if(event.key === this.trainText.charAt(this.currentIndex))
                this.success_keys.push(this.currentIndex);
            else
                this.error_keys.push(this.currentIndex);
            
            if(this.trainText.charAt(this.currentIndex+1)==='\n')
            this.currentIndex++;
            this.currentIndex++; 


            if(this.currentIndex>=this.trainText.length)
                alert("انتهى التدريب")

            
            this.inputs=[];
            let j=0;
        let i =0;
        for(let line of this.trainText.split('\n')) 
        {
            
            this.inputs.push([])
            for(let c of line)
                {

                    this.inputs[this.inputs.length-1].push([c,(this.currentIndex==(i+j)?'current':
                                                            this.error_keys.includes(i+j)?'errorkey':
                                                            this.success_keys.includes(i+j)?'success':'waiting')]);
                    i++;
                }
            
            j++;
        } 
        }
       }
       ,
       mounted(){
        window.addEventListener('keypress',this.updateText)
        let j=0;
        let i =0;
        for(let line of this.trainText.split('\n')) 
        {
            
            this.inputs.push([])
            for(let c of line)
                {
                    this.inputs[this.inputs.length-1].push([c,(this.currentIndex==(i+j)?'current':'')]);
                    i++;
                }
            
            j++;
        }   
            
        
       }
       ,
       created () {
            this.minutes= Math.floor( this.timer/60);
            this.seconds=this.timer%60;
           
        }


        
    }
</script>

<style>
    .current{
        background-color: skyblue;
    }
    .success{
        color: greenyellow;
    }
    .errorkey{
        color: red;
    }
  
  
</style>