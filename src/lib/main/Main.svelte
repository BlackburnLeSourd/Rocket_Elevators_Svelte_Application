<script>
import NFT1 from "./1.png";
import NFT2 from "./2.png";
import NFT3 from "./3.png";
</script>


<main >

    <div class="row">
        <div class="column">
          <img src={NFT1} alt="Snow" style="width:100%">
        </div>
    
        <div class="column">
          <img src={NFT2} alt="Forest" style="width:100%">
        </div>
        <div class="column">
          <img src={NFT3} alt="Mountains" style="width:100%">
        </div>
        <div class="content">
            <!-- <h2></h2> -->
            <p> NFT <br><br>Non-Fungible Tokens (NFTs) have exploded in popularity
              recently. In 2021, we saw a large number of NFT projects
              appear and the world became hooked. Several NFT platforms were
              created in 2021 and more and more Canadians have invested in 
              them. If you’re interested in buying NFTs, read on for our guide 
              to buying NFTs in Canada.</p>
          </div>
      </div>
      <div id="linear"> 
          <a href="/buy" class="btn">CLICK HERE TO HAVE ACCES TO WALLET</a>
         </div>
</main>

<style>

.row {
  display: flex;
  margin-top: 100px;
}

.column {
  flex: 33.33%;
  padding: 5px;
}

.content p {
    background-color: #245191;
    color: red;
    font-weight: bold;
    margin-top: 25px;
}

a.btn { width: 400px;
 padding: 10px 25px 10px 25px;
  font-family: Arial; 
  font-size: 16px;
   text-decoration: none;
    color: #ffffff; 
    background-color: red;

     }
      a.btn:hover {
           background-color: #245191; }

           #linear{
               display: flex;
               justify-content: center;
               padding-top: 40px;
               padding-bottom: 40px;
           }

</style> 