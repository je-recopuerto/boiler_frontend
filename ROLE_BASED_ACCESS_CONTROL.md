# Role-Based Access Control Implementation

## Overview
This implementation adds role-based access control to the BellyBasket admin dashboard, allowing different levels of access based on user permissions.

## Features Implemented

### 1. JWT Token Enhancement
- **Backend**: Updated login controller to include `admin` status in JWT token payload
- **Frontend**: Added JWT decoding utilities to extract user information and admin status

### 2. Authentication Context Enhancement
- Added `isAdmin` and `userInfo` to the AuthContext
- Automatic admin status detection on login and page refresh
- Token validation and user info extraction

### 3. Route Protection
- **Base Routes**: All users can access Sheet1 and Sheet2
- **Admin Routes**: Only admin users can access User table and CityName Tables
- **Protected Routes**: Enhanced ProtectedRoute component with admin requirement support

### 4. UI Updates
- **Navigation**: Admin-only menu items are hidden for non-admin users
- **Navbar**: Displays user name and admin badge for admin users
- **Access Control**: Non-admin users are redirected to Sheet1 when trying to access admin pages

## File Changes

### New Files Created
- `src/utils/jwtUtils.js` - JWT decoding utilities
- `src/utils/testJWT.js` - Testing utilities for JWT functionality
- `ROLE_BASED_ACCESS_CONTROL.md` - This documentation

### Modified Files
- `src/context/index.js` - Enhanced AuthContext with admin status
- `src/routes.js` - Dynamic routes based on admin status
- `src/App.js` - Updated to use dynamic routes
- `src/examples/ProtectedRoute/index.js` - Enhanced with admin requirements
- `src/examples/Navbars/DashboardNavbar/index.js` - Added user info display
- `Bellybasket_backend/controllers/authController.js` - Added admin status to JWT

## Usage

### For Admin Users
1. Login with admin credentials
2. Access all pages including User table and CityName Tables
3. See admin badge in navbar
4. Full navigation menu visible

### For Regular Users
1. Login with regular user credentials
2. Only access Sheet1 and Sheet2 pages
3. No admin badge in navbar
4. Limited navigation menu (admin items hidden)

## Testing

### JWT Testing
Open browser console and run:
```javascript
window.testJWT()
```

This will:
- Decode the current JWT token
- Display admin status
- Show user information

### Manual Testing
1. Login as admin user - should see all navigation items
2. Login as regular user - should only see Sheet1 and Sheet2
3. Try accessing admin pages as regular user - should be redirected to Sheet1
4. Check navbar for user info and admin badge

## Security Features

1. **Token Validation**: JWT tokens are validated on each page load
2. **Route Protection**: Admin-only routes are protected at the component level
3. **Navigation Control**: Admin-only menu items are conditionally rendered
4. **Automatic Redirects**: Non-admin users are redirected when accessing restricted pages

## Backend Requirements

Ensure the backend JWT_SECRET environment variable is set:
```env
JWT_SECRET=your_secret_key_here
```

## Frontend Requirements

The implementation uses:
- React Context for state management
- React Router for navigation
- Material-UI for components
- JWT decoding utilities

## Future Enhancements

1. **Role Hierarchy**: Support for multiple user roles
2. **Permission Granularity**: Fine-grained permissions for specific actions
3. **Audit Logging**: Track user actions and access attempts
4. **Session Management**: Enhanced session handling and token refresh 