create database dbHW2;
create table Supply
(
	id int not null, 
	name text, 
	unit text
)

create table Classes 
(
	id int not null, 
	name text,
	description text
)


create table Roles
(
	id int not null, 
	name text, 
	description text 
)

create table Users
(
	id int not null, 
	name text, 
	RoleID int not null
)

create table UserRoles
(
	UserID int not null,
	RoleID int not null
)

create table Locations 
(
	id int not null,
	name text
);

create table Status
(
	id int not null, 
	name text 
	
)

create table Guests 
(
	id int not null, 
	name text, 
	notes text, 
	BDay date, 
	CakeDay date, 
	StatusID int not null
)

create table Levels 
(
	id int, 
	GuestID int not null,
	ClassID int not null,
	DateGot date

)

create table Services
(
	id int not null, 
	name text, 
	StatusID int not null
);

create table Tavern 
(
	id int not null, 
	name text, 
	floors int, 
	OwnerID int not null,
	LocationID int not null
);

create table Recieved
(
	id int not null, 
	SupplyID int not null,
	TavernID int not null,
	cost money, 
	amtRec int not null, 
	dateRec date
);

create table Sales
(
	id int not null, 
	ServiceID int not null,
	GuestID int not null,
	TavernID int not null,
	price money, 
	datePur date, 
	amtPur int not null, 
)

create table Inventory 
(
	id int not null, 
	SupplyID int not null,
	TavernID int not null,
	DateRec date, 
	inInv int not null
	tried to title it count but it came back as a command?
)	

alter table Supply add primary key (id);
alter table Classes add primary key (id);
alter table Roles add primary key (id);

alter table Users add primary key (id);
alter table Users add foreign key (RoleID) references Roles(id);

alter table UserRoles add foreign key (UserID) references Users(id);
alter table UserRoles add foreign key (RoleID) references Roles(id);

alter table Locations add primary key (id);
alter table Status add primary key (id);

alter table Guests add primary key (id);
alter table Guests add foreign key (StatusID) references Status(id);

alter table Levels add primary key (id);
alter table Levels add foreign key (GuestID) references Guests(id);
alter table Levels add foreign key (ClassID) references Classes(id);

alter table Services add primary key (id);
alter table Services add foreign key (StatusID) references Status(id);

alter table Tavern add primary key (id);
alter table Tavern add foreign key (OwnerID) references Users(id);
alter table Tavern add foreign key (LocationID) references Locations(id);

alter table Recieved add foreign key (SupplyID) references Supply(id);
alter table Recieved add foreign key (TavernID) references Tavern(id);

alter table Sales add foreign key (ServiceID) references Services(id);
alter table Sales add foreign key (GuestID) references Guests(id);
alter table Sales add foreign key (TavernID) references Tavern(id);

alter table Inventory add foreign key (SupplyID) references Supply(id);
alter table Inventory add foreign key (TavernID) references Tavern(id);

alter table Levels 
alter column id int not null; 