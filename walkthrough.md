# Command Management & Auth Feature

## Authentication
The system now supports user authentication with two roles: **Admin** and **Operator**.
- **Guest**: View only.
- **Admin/Operator**: Can Add/Edit commands.

### Default Credentials
- **Username**: `admin`
- **Password**: `admin123`

### Database
A `users` table has been added to `commands.db`.
Columns: `id`, `username`, `password`, `role`.

## Verification Steps
1.  **Load Page**: You should see "Войти" (Login) button. "Добавить команду" (Add Command) and Edit (✎) buttons should be hidden.
2.  **Login**:
    - Click "Войти".
    - Enter `admin` / `admin123`.
    - Click "Войти".
    - Verify "Добавить команду" appears and "Войти" changes to "Выйти".
    - Verify "✎" buttons appear on commands.
3.  **Logout**:
    - Click "Выйти".
    - Verify buttons disappear.
4.  **Persistence**:
    - Refresh page while logged in. You should stay logged in.

## Technical Details
- **API**:
    - `POST /api/login.php`: Authenticates user.
    - `GET /api/logout.php`: Clears session.
    - `GET /api/check_auth.php`: Returns current user state.
    - `save_command.php` and `update_command.php` now require a valid session.
- **Frontend**:
    - `custom.js` manages global `USER` state.
    - UI updates automatically based on auth state.
