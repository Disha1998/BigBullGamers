# BigBullGamers 🤖 : "Platform for the next generation Games and Gamers" - Gamvertisment, RentNFT Assets and Interact with Gamers in Metaverse. 🌎


## Problem

In Blockchain Gaming, not being able to afford NFTs is becoming a “Big Barrier to Entry" for many players. 
With the adoption of the metaverse, the demand for virtual land NFTs are rising but there are no ways for long-term holders to be able to generate the value of their virtual lands

There are many games, generalized jobs platforms, and different gaming communities but no platform where Game Players, Builders,  Animation artists, Metaverse Virtual estate agents can interact and network with like minded individuals. 


## Our solution: 

**BigBullGamers** is a platform for next generation Gamers and Games where players, builders, animators, and investors can connect with each other, generate passive income by renting their in game assets, or by allowing Gamevertisement (Game Advertisement) on their virtual land NFTs. 

## How it works:

**Connect @ Metaverse:** At BigBullGamers, users will be able to visit virtual contests and can have text
and audio chat with virtual visitors of the metaverse across the globe.

**NFT Asset Rental:** A zero collateral rental platform to lend and Borrow Game NFT Assets. Another
option is collateral lending but because of huge price and volatility, Collateralized lending is not a
practical way rent NFTs. Eg: Not every individual can collateralize 150 Eth to use Cryptopunk.

**Gamervertisement: Gamvertisement is -> Advertisement** in Gaming. Here NFT owners can generate
passive income by allowing billboards like in game ads in blockchain games.

## Bounties Integration: 


**Polygon:** Polygon is always the go to choice for fast and affordable transactions in Gaming and we used it for our NFT rental service and game advertisement where users can buy ad space for a period of time and display ads in BBGs Metaverse.

#### https://github.com/mansijoshi17/BigBullGamers/blob/master/hardhat.config.js

**IPFS/Filecoin NFT.Storage:** Using NFT.Storage, we have stored  NFT meta data of our 1) Rental NFTs and 2) ad space NFT of Gamervertisment at BBGs metaverse. 

#### https://github.com/mansijoshi17/BigBullGamers/blob/master/components/Create.js

```
const NFTclient = new NFTStorage({

  token: process.env.NEXT_PUBLIC_NFT_STORAGE_API_KEY
  
});

 const metadata = await NFTclient.store({
 
        name: file.name,
        
        description: "NFT!",
        
        image: new File([file], file.name, { type: "image/jpg" }),
        
      });
      
```


**Superfluid:** Used superfluid streaming cash flow for monthly rental fees of our zero collateral nft rental service in BigBullGamers. 

#### https://github.com/mansijoshi17/BigBullGamers/blob/master/context/SuperfluidContext.js

```
async function createNewFlow(recipient, flowRate) {
    const provider = new ethers.providers.Web3Provide(window?.ethereum);
    const signer = provider.getSigner();
    setIsLoaing(true);
    const chainId = await window.ethereum.request({ method: "eth_chainId" });
    try {
      const sf = await Framework.create({
        chainId: Number(chainId),
        provider: provider,
      });
      const createFlowOperation = sf.cfaV1.createFlow({
        flowRate: flowRate,
        receiver: recipient,
        superToken: USDCx,
        // userData?: string
      });
      const result = await createFlowOperation.exec(signer);
      setIsLoaing(false);
      alert(`Congrats - you've just created a money stream!
        View Your Stream At: https://app.superfluid.finance/dashboard/${recipient}`);
    } catch (error) {
      setIsLoaing(false);
      alert(
        "Stream for this address is already exist! or may you don't have enough DAI"
      );
      console.error(error);
    }
  }
  function calFlowRate(amt) {
    console.log(amt);
    if (typeof Number(amt) !== "number" || isNaN(Number(amt)) === true) {
      throw new Error("calculate a flowRate based on a number");
    } else if (typeof Number(amt) === "number") {
      const monthlyAmount = ethers.utils.parseEther(amt.toString());
      const calculatedFlowRate = Math.floor(monthlyAmount / 3600 / 24 / 30);
      return calculatedFlowRate;
    }
  }
```

**Chainlink Price feed** is used to convert the price of tokens such as Matic to USD, Ether to USD while the user creates  NFTs.


#### https://github.com/mansijoshi17/BigBullGamers/blob/master/components/Create.js

```
 const provider = new ethers.providers.Web3Provider(window.ethereum);
    const signer = provider.getSigner();
    const priceFeed = new ethers.Contract(
      chainLinkPriceFeed,
      chainlinkABI,
      signer
    );
    setPriceFeedCon(priceFeed);
 if (priceFeedCon !== undefined) {
      getPrice();
    }
  async function getPrice() {
    let [price, decimals] = await priceFeedCon.getLatestPriceForMatic();
    price = Number(price / Math.pow(10, decimals)).toFixed(2);
    setUsdValue(price);
  }
```




## Screen Shots

<img width="1438" alt="MicrosoftTeams-image (25) (1)" src="https://user-images.githubusercontent.com/69969675/161445050-f3ecde29-9e17-4df3-9190-4a78c4c1f631.png">


<img width="1438" alt="MicrosoftTeams-image (24) (1)" src="https://user-images.githubusercontent.com/69969675/161445053-16543e1c-9fe0-42ac-aee7-cd887de9a660.png">


<img width="1438" alt="MicrosoftTeams-image (3) (1)" src="https://user-images.githubusercontent.com/69969675/161445054-cd89add5-6b21-49b3-881b-6bf4585a4faa.png">



![Screenshot from 2022-04-03 23-30-26](https://user-images.githubusercontent.com/69969675/161442015-696a51a8-5dca-489d-aa49-0f50fa67ba64.png)


![35d90212-8d08-4a2d-88a6-7eadaaa2d90c](https://user-images.githubusercontent.com/69969675/161446033-0f938454-9ef4-4c79-bae3-6a710415de2b.png)



![Screenshot from 2022-04-03 23-31-41](https://user-images.githubusercontent.com/69969675/161442020-29c73f5f-1b24-4f26-ab83-e200dc9e98cb.png)


![MicrosoftTeams-image (1)](https://user-images.githubusercontent.com/69969675/161442124-51eacc7b-00c5-4705-83db-bc71abd3a47c.png)


![MicrosoftTeams-image2](https://user-images.githubusercontent.com/69969675/161442126-8e48d844-f42a-4cbd-b91d-5f405065b396.png)




**WAGMI 😊🚀∞**
