# esnextstuff



Return a reversed copy of it


```js
const list = ['1st', 8, 9, 10]

const getHead = ([head]) => head  // ( ͡° ͜ʖ ͡°)  
const getTail = ([, ...tail]) => tail

const allButtFirst = getTail(list);
const firstEle = getHead(list);
```

things going on there...

1) destructuring
2) arrow functions
3) var dumping in destructuring ,
4) ( ͡° ͜ʖ ͡°) 


Spreading:
```js

```


Return a copy
```js
    const invertArray = array => [...array].reverse();
````





A Real World Example

```js
export const doGetUserByUid = async uid =>
    firestore
        .collection("users")
        .doc(uid)
        .get()
        .then(doc => doc.data())

export const doGetUserProfileByUid = async uid => {    
      let publicData = await doGetUserByUid(uid)
      let privateData = await doGetPrivateDataFromUser(uid)
      let allData = {...publicData, ...privateData}
      let userProfile =  PrivateProfile(allData)
      return userProfile
}
```

1) Arrow Functions
2) async Await
3) implicit Returns
4) promises
5) gathering/spread


Destructuring:


```
const pileOfGoo = {
  goo: 'goo',
  isToxic: true,
  name: 'pileOfGoo'
}

const randomUser = {
  name: 'Jack'
}

export const createUser = ({
  name = "NoName",
  isToxic = '',
  fetishes = {},
  photoURL = ""
} = {}) => ({
  name,
  private: {
    fetishes: {}
  },
  photoURL
})
```

``` js
import ChatMessage from "../../Molecules/ChatMessage/ChatMessage";

export const Conversation = ({ senderId, messages }) => {
    const getMessageContent = ({ parts : [{payload : {content}} = {}] = []}) => content
    const isReceiver = id => senderId === id ? 'left' : 'right'

    return (
        <Fragment>
          { messages.map((message,i) => 
              <ChatMessage key={i} 
                position={isReceiver(message.senderId)} 
                userName={message.senderId} 
                createdAt={message.createdAt}
                text={getMessageContent2(message)}/>
            )
          }
        </Fragment>
    )
}

export default Conversation
```

```js
export const doGetUserMessagesByRoomId = async (roomId = '') => {
    let currentUser = await doGetCurrentUser()
    return currentUser.fetchMultipartMessages({
          roomId: roomId,
          limit: 100,
      }).then(messages => messages)
}

```

```js
export const doGetDevsFromFirestore = () =>
    firestore
        .collection("users")
        .where("isDev", "==", true)
        .get()
        .then(snapshot =>
            snapshot.docs.map(documentSnapshot => documentSnapshot.data())
        )
```


``` js
import { doGetUserMessagesByRoomId } from "../../../chat/chatkit/chatkit";


const fetchMessages = async (roomId) => { 
        setIsLoading(true)
        let messages = await doGetUserMessagesByRoomId(roomId)
        setIsLoading(false)
        return messages
}
```js
export const doGetContactListFromUserByUid = uid =>
    firestore
        .collection("users")
        .doc(uid)
        .collection("contacts")
        .get()
        .then(snapshot => snapshot.docs.map(documentSnapshot => documentSnapshot.data()))
```
