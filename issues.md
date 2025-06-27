Great! Here's a **refactored GitHub issue ticket set** to build a **Blog Platform** using:

- 📱 **Frontend**: React Native (mobile app)
- 🚀 **Backend**: Go + Gin
- 🗄️ **Database**: PostgreSQL
- 📦 **Deployment**: Kubernetes (K8s)

---

## 🗂️ Epic: Project Setup

---

### ✅ Issue: Initialize React Native and Go Project

**Title**: Setup React Native and Go Gin project structure
**Description**:

- Initialize Go project (`go mod init`) and setup Gin.
- Initialize React Native app using Expo or React Native CLI.
- Create folders: `mobile/` (React Native), `server/` (Go).
- Add `.gitignore`, README files for both.

---

### ✅ Issue: Docker and Kubernetes Setup

**Title**: Add Dockerfiles and K8s manifests for backend
**Description**:

- Create Dockerfile for Gin backend.
- Write K8s `deployment.yaml`, `service.yaml`, `configmap.yaml`, `secret.yaml`.
- Configure PostgreSQL credentials via Secrets.
- Setup PostgreSQL StatefulSet and PVC.
- (Optional) Add Ingress for backend API access.

---

## 👤 Epic: User Authentication

---

### ✅ Issue: User Model and Migration

**Title**: Define `users` table and DB schema
**Description**:

- Fields: `id`, `username`, `email`, `password_hash`, `created_at`.
- Use SQL migrations with tools like `golang-migrate`.
- Setup PostgreSQL connection in Gin backend.

---

### ✅ Issue: Register API

**Title**: POST /api/register - User registration
**Description**:

- Receive username, email, and password.
- Hash password using bcrypt.
- Save to DB and return JWT.

---

### ✅ Issue: Login API

**Title**: POST /api/login - User login
**Description**:

- Accept email and password.
- Authenticate and return JWT token.
- Use cookie or return via JSON.

---

### ✅ Issue: Auth Middleware for Gin

**Title**: JWT middleware to protect private routes
**Description**:

- Parse JWT from Authorization header.
- Validate and extract user ID.
- Protect all post/comment creation APIs.

---

### ✅ Issue: Auth Flow in React Native

**Title**: Setup auth context in mobile app
**Description**:

- Create React Context for user/auth state.
- Handle login, logout, and registration.
- Store token securely (e.g. `AsyncStorage` or `SecureStore`).
- Auto-redirect on login/logout.

---

## ✍️ Epic: Blog Post CRUD

---

### ✅ Issue: Post Model and Migration

**Title**: Create `posts` table migration
**Description**:

- Fields: `id`, `title`, `content`, `author_id`, `created_at`, `updated_at`.

---

### ✅ Issue: Create Post API

**Title**: POST /api/posts - Add a new blog post
**Description**:

- Auth required.
- Save title/content with logged-in user ID.
- Return the created post.

---

### ✅ Issue: List All Posts API

**Title**: GET /api/posts - List all blog posts
**Description**:

- Return all posts with author info.
- Add pagination support (optional).

---

### ✅ Issue: Get Post by ID API

**Title**: GET /api/posts/\:id - View single post
**Description**:

- Return post by ID with author and timestamp.

---

### ✅ Issue: Update/Delete Post API

**Title**: PUT /api/posts/\:id & DELETE /api/posts/\:id
**Description**:

- Auth required.
- Only post owner can edit or delete.

---

### ✅ Issue: Mobile UI for Posts

**Title**: List, view, create, and edit blog posts in React Native
**Description**:

- Screens: Home (list), View Post, Create/Edit Post.
- Use Axios or Fetch for API calls.
- Form input with validation.

---

## 💬 Epic: Comments

---

### ✅ Issue: Comment Model and Migration

**Title**: Create `comments` table schema
**Description**:

- Fields: `id`, `post_id`, `author_id`, `content`, `created_at`.

---

### ✅ Issue: Add Comment API

**Title**: POST /api/posts/\:id/comments
**Description**:

- Auth required.
- Save comment under the post.
- Return comment with author info.

---

### ✅ Issue: List Comments API

**Title**: GET /api/posts/\:id/comments
**Description**:

- Fetch all comments for a given post.

---

### ✅ Issue: Show/Add Comments in Mobile UI

**Title**: Implement comment list and input in post screen
**Description**:

- Authenticated users can add a comment.
- Show list with commenter and timestamp.

---

## 🎨 Epic: UI/UX in React Native

---

### ✅ Issue: React Native Navigation Setup

**Title**: Add stack navigation for screens
**Description**:

- Use `react-navigation`.
- Screens: Login, Register, Home, Post Detail, Create/Edit Post, My Posts.
- Handle navigation based on auth state.

---

### ✅ Issue: Design Consistent Layout & Styling

**Title**: Apply clean layout and design
**Description**:

- Use consistent padding, typography, and button styles.
- Support light/dark themes (optional).
- Use `react-native-paper` or `nativewind` for styling components.

---

### ✅ Issue: Show Toast Notifications

**Title**: Add feedback using `react-native-toast-message`
**Description**:

- Show success/error messages for actions like login, post create/delete, comment etc.

---

## 🚀 Epic: Deployment

---

### ✅ Issue: Deploy PostgreSQL in Kubernetes

**Title**: PostgreSQL K8s StatefulSet with PVC
**Description**:

- Use persistent volume with storage class.
- Add secret/config for DB credentials.
- Expose via ClusterIP internally.

---

### ✅ Issue: Deploy Gin API to Kubernetes

**Title**: Backend K8s deployment and service
**Description**:

- Add Dockerfile for backend.
- Create Deployment and Service YAML.
- Mount env vars via Secrets and ConfigMap.

---

### ✅ Issue: Mobile App Build + Environment Config

**Title**: Configure mobile app for API environment
**Description**:

- Use `.env` files or constants for base URL.
- Handle production vs local dev base URLs (e.g., via Expo constants).

---

### ✅ Issue: Expose Backend with Ingress

**Title**: Add Ingress config for API
**Description**:

- Use Ingress Controller.
- Add domain + TLS (via cert-manager).
- Route `/api/*` to Gin backend.

---

### ✅ Issue: Release Mobile App (Optional)

**Title**: Prepare mobile app build for testing/release
**Description**:

- Setup Expo EAS or React Native CLI build process.
- Generate APK/IPA builds for Android/iOS.
- Optional: Upload to Play Store / TestFlight.

---
