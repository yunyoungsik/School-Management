# School Management

[참고영상1](https://www.youtube.com/watch?v=myYlGLFxZas)
[참고영상2](https://youtu.be/6sfiAyKy8Jo?si=t6zCfN43vr0UDJOw)

## 설치
```
npm i recharts    
npm i react-calendar    
npm i react-big-calendar moment    
npm i @types/react-big-calendar    
npm i react-hook-form zod @hookform/resolvers
```
```
npm i prisma
npx prisma init
```

## PRISMA
### 1. `autoincrement()`
`autoincrement()`는 데이터베이스에서 숫자 필드가 **자동으로 증가**하도록 설정하는 기능입니다.  
주로 **ID 필드**와 같은 Primary Key에 사용됩니다.

#### 사용예시
```prisma
model Lesson {
  id   Int    @id @default(autoincrement())
  name String
}
```

### 2. `@relation`
@relation은 두 모델 간의 **외래 키 관계(Foreign Key Relationship)**를 설정합니다.

#### 사용예시
```prisma
model Lesson {
  id        Int     @id @default(autoincrement())
  name      String
  subjectId Int
  subject   Subject @relation(fields: [subjectId], references: [id])
}

model Subject {
  id    Int     @id @default(autoincrement())
  name  String
  description String
}
```

### 3. `enum`
enum(열거형)은 값의 선택지를 제한하는 데이터 타입입니다.
이런 유효한 값 목록을 미리 정의하여 사용자가 유효하지 않은 값을 입력하는 실수를 방지합니다.

#### 사용예시
```prisma
enum UserSex {
  MALE
  FEMALE
}

model Student {
  id   Int     @id @default(autoincrement())
  name String
  sex  UserSex
}
```
