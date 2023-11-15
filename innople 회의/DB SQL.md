
drop table EMPLOYEE;

CREATE TABLE employee(
id bigint AUTO_INCREMENT,
first_name VARCHAR(255),
last_name VARCHAR(255),
email VARCHAR(255),
PRIMARY KEY (id)
);


INSERT INTO employee VALUES(default, 'Leslie', 'Andrews', 'leslie@luv2code.com');
INSERT INTO employee VALUES(default, 'Emma', 'Baumgarten', 'emma@luv2code.com');
INSERT INTO employee VALUES(default, 'Avani', 'Gupta', 'ag@luv2code.com');
INSERT INTO employee VALUES(default, 'Pet', 'rollium', 'pr@luv2code.com');
INSERT INTO employee VALUES(default, 'V', 'punkie', 'vp@luv2code.com');


테이블이 존재하는 경우 삭제하기
새 테이블 만들기
  컬럼은 ID와 NAME
행 추가
행 추가
테이블 질의
행 데이터 변경
행 삭제	
ROP TABLE IF EXISTS TEST;
CREATE TABLE TEST(ID INT PRIMARY KEY,
   NAME VARCHAR(255));
INSERT INTO TEST VALUES(1, 'Hello');
INSERT INTO TEST VALUES(2, 'World');
SELECT * FROM TEST ORDER BY ID;
UPDATE TEST SET NAME='Hi' WHERE ID=1;
DELETE FROM TEST WHERE ID=2;

=============================================
DROP TABLE IF EXISTS `authorities`;
DROP TABLE IF EXISTS `users`;

--
-- Table structure for table `users`
--

CREATE TABLE users (
  username varchar(50) NOT NULL,
  password varchar(68) NOT NULL,
  enabled tinyint NOT NULL,
  PRIMARY KEY (username)
);

--
-- Inserting data for table `users`
--

INSERT INTO users
VALUES 
('john','{bcrypt}$2a$10$qeS0HEh7urweMojsnwNAR.vcXJeXR1UcMRZ2WcGQl9YeuspUdgF.q',1),
('mary','{bcrypt}$2a$10$qeS0HEh7urweMojsnwNAR.vcXJeXR1UcMRZ2WcGQl9YeuspUdgF.q',1),
('susan','{bcrypt}$2a$10$qeS0HEh7urweMojsnwNAR.vcXJeXR1UcMRZ2WcGQl9YeuspUdgF.q',1);




--
-- Table structure for table `authorities`
--

CREATE TABLE authorities (
  username varchar(50) NOT NULL,
  authority varchar(50) NOT NULL,
  CONSTRAINT authorities_idx_1 UNIQUE (username, authority),
  CONSTRAINT authorities_ibfk_1 FOREIGN KEY (username) REFERENCES users (username)
);

--
-- Inserting data for table `authorities`
--

INSERT INTO authorities
VALUES 
('john','ROLE_EMPLOYEE'),
('mary','ROLE_EMPLOYEE'),
('mary','ROLE_MANAGER'),
('susan','ROLE_EMPLOYEE'),
('susan','ROLE_MANAGER'),
('susan','ROLE_ADMIN');



=============================================


DROP TABLE IF EXISTS roles;
DROP TABLE IF EXISTS members;

--
-- Table structure for table ``members`;`
--

CREATE TABLE members (
  user_id varchar(50) NOT NULL,
  pw varchar(68) NOT NULL,
  active tinyint NOT NULL,
  PRIMARY KEY (user_id)
);

--
-- Inserting data for table ``members`;`
--

INSERT INTO members
VALUES 
('john','{bcrypt}$2a$10$qeS0HEh7urweMojsnwNAR.vcXJeXR1UcMRZ2WcGQl9YeuspUdgF.q',1),
('mary','{bcrypt}$2a$10$qeS0HEh7urweMojsnwNAR.vcXJeXR1UcMRZ2WcGQl9YeuspUdgF.q',1),
('susan','{bcrypt}$2a$10$qeS0HEh7urweMojsnwNAR.vcXJeXR1UcMRZ2WcGQl9YeuspUdgF.q',1);




--
-- Table structure for table roles
--

CREATE TABLE roles (
  user_id varchar(50) NOT NULL,
  role varchar(50) NOT NULL,
  CONSTRAINT authorities5_idx_1 UNIQUE (user_id, role),
  CONSTRAINT authorities5_ibfk_1 FOREIGN KEY (user_id) REFERENCES members (user_id)
);

--
-- Inserting data for table `rolesroles`
--

INSERT INTO roles
VALUES 
('john','ROLE_EMPLOYEE'),
('mary','ROLE_EMPLOYEE'),
('mary','ROLE_MANAGER'),
('susan','ROLE_EMPLOYEE'),
('susan','ROLE_MANAGER'),
('susan','ROLE_ADMIN');


http://svn.elandsystems.com:8090/scm/git/EXMPLAPI
http://ci.elandsystems.com/view/BBPO/


INSERT INTO CONTACT 
VALUES 
('true','john','01087651111')



INSERT INTO authorities
VALUES 
('Han.SungYoup01','ROLE_ADMIN'),


insert into contact (id, create_time, creator, update_time, updater, is_new, name, phone) values(1, parsedatetime('2023-08-30 08:47:52.69', 'yyyy-MM-dd hh:mm:ss.SS'), 'han.sungyoup01', null, null, true, 'mike han', '010-2222-3333');



http://svn.elandsystems.com:8090/scm/svn/2023/CNHRLINK_Project