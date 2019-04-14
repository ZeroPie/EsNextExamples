# esnextstuff



Return a reversed copy of it

const invertArray = array => [...array].reverse();



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
