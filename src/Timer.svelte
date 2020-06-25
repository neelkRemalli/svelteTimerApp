<script>
     import ProgressBar from './Progress.svelte'
     const totalSecond = 20;
     let secondLeft = totalSecond;
     $:progressBar = ((totalSecond - secondLeft)/totalSecond) * 100;
     let isRunning = false
    
    const handleTimer = () =>{
        isRunning = true
        const timer = setInterval(()=>{
            
           secondLeft -= 1;
           if(secondLeft <= 0){
               clearInterval(timer)
               isRunning = false
               secondLeft = totalSecond;
           }
        },1000)
       
    }
    
    
</script>

  
  <div bp="grid">
      
    <h2 bp="offset-5@md 4@md 12@sm">Seconds Left:{secondLeft} </h2>
  </div>
  <ProgressBar {progressBar} />
  
  <div bp="grid">
  
    <button
      bp="offset-5@md 4@md 12@sm"
      class="start"
      on:click={handleTimer}
      disabled={isRunning}
      >
      Start
    </button>
  
  </div>
  
<style>
    h2 {
      margin: 0;
    }
    .start {
      background-color: rgb(154, 73, 73);
      width: 100%;
      margin: 10px 0;
    }
    .start[disabled]{
        background-color: #eee;
        cursor: not-allowed;
    }
  
  </style>
 