```mermaid
classDiagram
    class ClientApp {
        +connectToServer()
        +sendAudioVideo()
        +receiveAudioVideo()
        +joinRoom(roomId: String)
        +leaveRoom()
    }

    class Server {
        +manageRooms()
        +handleConnections()
        +relayAudioVideo()
        +authenticateUser()
        +disconnectUser()
    }

    class Database {
        +storeUserDetails()
        +storeRoomDetails()
        +storeMessageHistory()
    }

    class Room {
        +roomId: String
        +participants: List<User>
        +addParticipant(user: User)
        +removeParticipant(user: User)
    }

    class User {
        +userId: String
        +username: String
        +connect()
        +disconnect()
    }

    %% Relationships %%
    ClientApp --> Server : Communicates via WebSocket
    Server --> Database : Stores and retrieves data
    Server --> Room : Manages room creation and participant interactions
    Room --> User : Has participants

    %% Highlight interaction between two users %%
    User --> Room : Joins/Leaves
    Room ..> User : Relays audio/video
