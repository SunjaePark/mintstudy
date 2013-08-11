## Objects

### sqlite3_stmt







## Function

### sqlite3_open

	int sqlite3_open(
		const char *filename,   /* Database filename (UTF-8) */
		sqlite3 **ppDb          /* OUT: SQLite db handle */
	);

* filename arguments로 지정한 SQLite database file을 연다.
* error가 발생한 경우에도 보통 database connection handle은 *ppDB에 반환된다.
* 유일한 예외는 SQLite 객체를 유지하기 위한 memory를 할당 할 수 없는 경우, sqlite3 object의 pointer 대신에 *ppDb에 NULL이 기록된다.
* 성공적으로 database를 **열였을(그리고 / 또는 만들었을) 경우 SQLITE_OK가 반환**된다.
* 그렇지 않은 경우 Error Code가 반환된다.
* sqlite3_errmsg() 루틴은 sqlite3_open() 루틴에서 발생하는 어떤 error에 대한 영어 설명을 얻는데 사용할 수 있다.

-----

### sqlite3_exec

	int sqlite3_exec(
		sqlite3*,                                  /* An open database */
		const char *sql,                           /* SQL to be evaluated */
		int (*callback)(void*,int,char**,char**),  /* Callback function */
		void *,                                    /* 1st argument to callback */
		char **errmsg                              /* Error msg written here */
	);


-----

### sqlite3_prepare_v2




-----

### sqlite3_bind_int



-----

### sqlite3_bind_text



-----

### sqlite3_step




-----

### sqlite3_finalize





-----

### sqlite3_close





### bind

* 쿼리로 데이터베이스를 불러올때 조건문이 있을 경우 보통 명령줄(query)에 전부 넣는다.

		SELECT * FROM table WHERE id=1 AND type='home'

* bind를 사용하는 경우 SQL쿼리를 미리 만들어 넣어서 돌리고 조건문의 경우 그 값들을 나중에 넣어주게 됩니다

		SELECT * FROM table WHERE id=? AND type=?
			bind 1, 0
			bind "home", 1
			
