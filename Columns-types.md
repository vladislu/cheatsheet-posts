---
title: Columns types 
categories: 
  - Typeorm
date: 2021-08-01 21:10:11
tag: [tag1]
version: cheatSheets
github: Columns-types 
---

## get started

## Columns types

### Default Columns

```js
	// Create Primary Key from id value
    @PrimaryColumn()
    id: number;
	
	// Create Primary Key for id by incremental number 
    @PrimaryGeneratedColumn()
    id: number;
	
	// Create Primary Key for id by uuid type 
    @PrimaryGeneratedColumn("uuid")
    id: number;
	
	// Create firstName Column type string
    @Column()
    firstName: string;
	
	// Create isActive Column type boolean
    @Column()
    isActive: boolean;
```

### Special columns

```js
	// automatically set to the entity's insertion date
	@CreateDateColumn()
	created_at: Date;
	
	// automatically set to the entity's update time each time you call save 
	@UpdateDateColumn()
	updated_at: Date;
	
	// automatically set to the entity's delete time each time you call soft-delete
	@DeleteDateColumn ()
	deleted_at: Date;
	
	// automatically set to the entity's version number and increase it each time you call save
	@VersionColumn ()
	version: Date;
```

### columns by parameters 

```js
	// set column type as int
	@Column("int")
	
	// or this way
	@Column({ type: "int" })
	
	// set column type as varchar char length 200
	@Column("varchar", { length: 200 })
	
	// or this way for integer
	@Column({ type: "int", width: 200 })
```

### enum column

```js
// Using typescript enums
export enum UserRole {
    ADMIN = "admin",
    EDITOR = "editor",
    GHOST = "ghost"
}

@Entity()
export class User {

    @PrimaryGeneratedColumn()
    id: number;

    @Column({
        type: "enum",
        enum: UserRole,
        default: UserRole.GHOST
    })
    role: UserRole
}
```

```js
// Using array with enum values
export type UserRoleType = "admin" | "editor" | "ghost",

@Entity()
export class User {

    @PrimaryGeneratedColumn()
    id: number;

    @Column({
        type: "enum",
        enum: ["admin", "editor", "ghost"],
        default: "ghost"
    })
    role: UserRoleType
}
```
