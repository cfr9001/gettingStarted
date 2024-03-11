```plantuml

@startuml innP

abstract class Base {
    Id: Guid
    CreatedAt: DateTime
}

enum UserRoleType {
    Admin
    User
}

class ChangeHistory {
    UpdatedAt: DateTime
}

class User {
    Firstname: string
    Lastname: string
    Age: int
    Birthday: DateOnly
    UserRole: UserRoleType
    Address: Address
    AreaCode: int
    MobileNumber: int
    Email: MailAddress
}

class Address {
    Street: string
    HouseNumber: string
    Additional: string
    PostalCode: int
    City: string
    Country : string
}

class Event {
    Title: string
    Description: string
    EventStart: DateTime
    EventEnd: DateTime
    MinParticipants: int
    MaxParticipants: int
    Location: Address
    RegistrationDeadline: DateTime
}

class Chat {
    Message: string
}

class Blocked {

}

class ReportedUser {
    Description: string
}

class Interest {
    Name: string
}

class Post {
    Message
}


class User extends Base
class Event extends Base
class Address extends Base
class User extends UserRoleType
class Chat extends Base
class Post extends Base
class ReportedUser extends Base
class Blocked extends Base
User "1" o--- "0..*" Event : creates
Event "0..*" --- "0..*" User : has participants
User "0..*" --- "0..*" User : follows
Event "1" o--- "0..*" Address : has
User "0..*" --- "0..*" Interest : has
Event "1" o--- "1" Chat : has
Chat "1" o--- "1" User : has
Chat "0..*" --- "0..*" Event : has
Post "0..*" --- "0..*" User : has

@enduml