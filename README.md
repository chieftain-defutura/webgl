# Battle API endpoints

These endpoints allow you to get the Battle data.

### User Endpoints

| Method | URL                                                     | Description                                     |
| ------ | ------------------------------------------------------- | ----------------------------------------------- |
| `GET`  | [/api/battles/upcoming](#get-apibattlesupcoming)        | Retrieve all the upcoming battles               |
| `GET`  | [/api/battles/ongoing](#get-apibattlesongoing)          | Retrieve all the ongoing battles                |
| `GET`  | [/api/battles/previous](#get-apibattlesprevious)        | Retrieve all the previous battles               |
| `GET`  | [/api/battle/:battleId](#get-apibattlebattleid)         | Retrieve the battle data by battle id           |
| `GET`  | [/api/battles/:date-filter](#get-apibattlesdate-filter) | Retrieve the battles based on the provided date |

### GET /api/battles/upcoming

**Request**
**Query**

| Name            | Required |  Type  | Description                                                                  |
| --------------- | :------: | :----: | ---------------------------------------------------------------------------- |
| `walletAddress` | required | string | walletAddress of a user to get the info of a user for that particular battle |

#### Response

    {
       data: [BattleInterface]
    }

### GET /api/battles/ongoing

**Request**
**Query**

| Name            | Required |  Type  | Description                                                                  |
| --------------- | :------: | :----: | ---------------------------------------------------------------------------- |
| `walletAddress` | required | string | walletAddress of a user to get the info of a user for that particular battle |

#### Response

    {
       data: [BattleInterface]
    }

### GET /api/battles/previous

**Request**
**Query**

| Name            | Required |  Type  | Description                                                                  |
| --------------- | :------: | :----: | ---------------------------------------------------------------------------- |
| `walletAddress` | required | string | walletAddress of a user to get the info of a user for that particular battle |

#### Response

    {
       data: [BattleInterface]
    }

#### GET /api/battle/:battleId

**Request**
**Parameters**

| Name       | Required |  Type  | Description                                               |
| ---------- | :------: | :----: | --------------------------------------------------------- |
| `battleId` | required | string | The battle id to retrieve the info of a particular battle |

#### Response

    {
        data:{
            BattleInterface & {
                participants: [Participants]
            }
        }
    }

### GET /api/battles/date-filter

**Request**
**Query**

| Name   | Required |  Type  | Description                             |
| ------ | :------: | :----: | --------------------------------------- |
| `date` | required | string | battle date to filter on that day alone |

#### Response

    {
       data: [BattleInterface]
    }

### Interfaces

**BattleInterface**

    {
        id: string;
        battleId: string;
        battleType: "HEALTH" | "BLOOD";
        battleStatus: string;
        exchange: string;
        country: string;
        startTime: number;
        endTime: number;
        totalParticipants: number;
        entryfee: number;
        nftCount: string;
        owner:{
            id: string
        };
        isJoined: boolean;
        userNft: [BillionsNft];
        userScalarNft: [ScalarNft];
        rewardAmount: number;
        isRewardClaimed: boolean;
        rank: number | null;
        totalRewardPool: number;
    }

**BillionsNft**

    {
        disable: boolean
        _id: string
        CEO?: string
        address: string
        city: string
        color: string
        country: string
        description: string
        employees: number
        exchange: string
        industry: string
        mic_code: string
        name: string
        symbolname: string
        phone?: string
        sector: string
        state?: string
        symbol: string
        type: string
        website?: string
        symbolExchange: string
        updatedAt?: string
        id: string
        tokenId: string
        stockSymbol: string
        rentPrice: number
        sellingPrice: number
        rentable: boolean
        isOnsale: boolean
        zip?: string
        createdAt?: string
        __v?: number
    }

**ScalarNft**

    {
        id: string
        tokenId: string
        value: string
    }

**Participants**

    {
        id: string
        rank: number | null
        isRewardClaimed: boolean
        rewardAmount: number
        battle:{
            id: string
            battleId: string
            battleType: "HEALTH"|"BLOOD"
            startTime: number
            country: string
            exchange: string
        }
    }
