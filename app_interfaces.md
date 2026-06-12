# App Interfaces

Format: `path: L<line>: <match_text>` where path is codebase-relative.

## Inbound Constructs

### http_endpoint (fastapi)

- `backend/app/api/routes/items.py`: L13: @router.get("/", response_model=ItemsPublic)
- `backend/app/api/routes/items.py`: L48: @router.get("/{id}", response_model=ItemPublic)
- `backend/app/api/routes/items.py`: L61: @router.post("/", response_model=ItemPublic)
- `backend/app/api/routes/items.py`: L75: @router.put("/{id}", response_model=ItemPublic)
- `backend/app/api/routes/items.py`: L99: @router.delete("/{id}")
- `backend/app/api/routes/login.py`: L100: @router.post( "/password-recovery-html-content/{email}", dependencies=[Depends(get_current_active_superuser)], response_class=HTMLResponse, )
- `backend/app/api/routes/login.py`: L23: @router.post("/login/access-token")
- `backend/app/api/routes/login.py`: L45: @router.post("/login/test-token", response_model=UserPublic)
- `backend/app/api/routes/login.py`: L53: @router.post("/password-recovery/{email}")
- `backend/app/api/routes/login.py`: L77: @router.post("/reset-password/")
- `backend/app/api/routes/private.py`: L23: @router.post("/users/", response_model=UserPublic)
- `backend/app/api/routes/users.py`: L103: @router.patch("/me/password", response_model=Message)
- `backend/app/api/routes/users.py`: L124: @router.get("/me", response_model=UserPublic)
- `backend/app/api/routes/users.py`: L132: @router.delete("/me", response_model=Message)
- `backend/app/api/routes/users.py`: L146: @router.post("/signup", response_model=UserPublic)
- `backend/app/api/routes/users.py`: L162: @router.get("/{user_id}", response_model=UserPublic)
- `backend/app/api/routes/users.py`: L182: @router.patch( "/{user_id}", dependencies=[Depends(get_current_active_superuser)], response_model=UserPublic, )
- `backend/app/api/routes/users.py`: L214: @router.delete("/{user_id}", dependencies=[Depends(get_current_active_superuser)])
- `backend/app/api/routes/users.py`: L32: @router.get( "/", dependencies=[Depends(get_current_active_superuser)], response_model=UsersPublic, )
- `backend/app/api/routes/users.py`: L54: @router.post( "/", dependencies=[Depends(get_current_active_superuser)], response_model=UserPublic )
- `backend/app/api/routes/users.py`: L81: @router.patch("/me", response_model=UserPublic)
- `backend/app/api/routes/utils.py`: L11: @router.post( "/test-email/", dependencies=[Depends(get_current_active_superuser)], status_code=201, )
- `backend/app/api/routes/utils.py`: L29: @router.get("/health-check/")

## Outbound Constructs

No outbound constructs detected.

## Internal Constructs

### relational_database.relationship (sqlmodel)

- `backend/app/models.py`: L56: Relationship(back_populates="owner", cascade_delete=True)
- `backend/app/models.py`: L96: Relationship(back_populates="items")
