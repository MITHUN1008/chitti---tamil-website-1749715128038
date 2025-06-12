# AI Website Builder - Comprehensive Documentation

## Project Overview
This is an AI-powered website builder that creates modern, responsive websites using YouTube channel data.

## Supabase Database Tables

### Core Tables

#### `profiles`
- Stores user profile information
- Columns: id, email, full_name, role, avatar_url, created_at, updated_at
- Purpose: User management and authentication

#### `projects`
- Stores website projects created by users
- Columns: id, user_id, name, description, youtube_url, channel_data, source_code, github_url, netlify_url, status, created_at, updated_at
- Purpose: Project management and tracking

#### `project_chat_history`
- Stores chat conversations between users and AI
- Columns: id, project_id, user_id, message_type, content, metadata, created_at
- Purpose: Chat history and conversation tracking

### API Key Management Tables

#### `youtube_api_keys`
- Stores YouTube Data API keys
- Columns: id, user_id, name, api_key, quota_used, quota_limit, is_active, last_used_at, created_at, updated_at
- Purpose: YouTube channel data fetching

#### `openrouter_api_keys`
- Stores OpenRouter API keys for AI responses
- Columns: id, user_id, name, api_key, credits_used, credits_limit, requests_count, is_active, last_used_at, created_at, updated_at
- Purpose: AI chat and code generation

#### `github_api_keys`
- Stores GitHub personal access tokens
- Columns: id, user_id, name, api_token, rate_limit_used, rate_limit_limit, is_active, last_used_at, created_at, updated_at
- Purpose: Repository creation and management

#### `netlify_api_keys`
- Stores Netlify API tokens
- Columns: id, user_id, name, api_token, deployments_count, deployments_limit, is_active, last_used_at, created_at, updated_at
- Purpose: Website deployment and hosting

### Monitoring and Analytics Tables

#### `api_usage_logs`
- Tracks API usage across all services
- Columns: id, user_id, provider, model, tokens_used, cost_usd, response_time_ms, status, error_message, created_at
- Purpose: Usage monitoring and cost tracking

#### `analytics`
- Stores user behavior and system analytics
- Columns: id, user_id, event_type, event_data, created_at
- Purpose: Analytics and insights

#### `audit_logs`
- Tracks system changes and user actions
- Columns: id, user_id, resource_type, resource_id, action, old_values, new_values, ip_address, user_agent, created_at
- Purpose: Security and compliance

### Deployment and Infrastructure Tables

#### `deployment_tokens`
- Stores deployment service tokens
- Columns: id, user_id, provider, token_name, token_value, is_active, created_at, updated_at
- Purpose: Multi-provider deployment management

#### `deployments`
- Tracks deployment history
- Columns: id, project_id, user_id, status, url, created_at
- Purpose: Deployment tracking

#### `domain_management`
- Manages custom domains
- Columns: id, user_id, domain_name, status, verification_token, dns_configured, ssl_enabled, created_at, updated_at
- Purpose: Custom domain management

### Configuration Tables

#### `email_configurations`
- Email service configurations
- Columns: id, user_id, provider, smtp_host, smtp_port, smtp_username, smtp_password, from_email, is_active, created_at, updated_at
- Purpose: Email notifications and communications

#### `webhook_endpoints`
- Webhook configurations
- Columns: id, user_id, name, url, events, secret, is_active, last_triggered_at, created_at, updated_at
- Purpose: Event notifications and integrations

#### `backup_schedules`
- Automated backup configurations
- Columns: id, user_id, name, backup_type, schedule_cron, last_run_at, next_run_at, is_active, created_at, updated_at
- Purpose: Data backup and recovery

### System Tables

#### `system_monitoring`
- System performance metrics
- Columns: id, metric_name, metric_value, metric_unit, metadata, recorded_at
- Purpose: System health monitoring

#### `storage_usage_tracking`
- File storage usage tracking
- Columns: id, user_id, bucket_name, file_count, total_size_bytes, last_updated
- Purpose: Storage usage monitoring

#### `file_storage`
- File metadata and storage paths
- Columns: id, user_id, file_name, file_type, file_size, storage_path, public_url, metadata, created_at, updated_at
- Purpose: File management

## Database Functions

### `handle_new_user()`
- Automatically creates user profiles when new users register
- Assigns admin role to specific email addresses
- Ensures proper user initialization

### `get_current_user_role()`
- Security definer function to get current user's role
- Used for role-based access control
- Returns user role for authorization

### `handle_updated_at()` / `update_updated_at_column()`
- Trigger functions to automatically update timestamps
- Maintains data consistency
- Tracks record modification times

## Features

### Real-time AI Code Generation
- Uses OpenRouter API for AI responses
- Generates HTML, CSS, and JavaScript code
- Supports multiple AI models and providers

### GitHub Integration
- Automatic repository creation
- Code versioning and history
- Collaborative development support

### Netlify Deployment
- Instant website hosting
- Automatic SSL certificates
- Global CDN distribution

### YouTube Integration
- Channel data fetching
- Thumbnail and metadata extraction
- Video content integration

## Security Features

### Row Level Security (RLS)
- All tables have appropriate RLS policies
- Users can only access their own data
- Admin users have elevated permissions

### API Key Management
- Secure storage of API credentials
- Usage tracking and rate limiting
- Key rotation and lifecycle management

### Audit Logging
- Complete audit trail of all actions
- Security monitoring and compliance
- User activity tracking

## Deployment Information

- **Created**: 2025-06-12T07:58:48.038Z
- **Platform**: Supabase + React + Vite
- **Hosting**: Netlify
- **Repository**: GitHub
- **AI Provider**: OpenRouter

## Environment Variables

All sensitive data is stored in Supabase secrets:
- `OPENROUTER_API_KEY`: AI model access
- `SUPABASE_URL`: Database connection
- `SUPABASE_ANON_KEY`: Public database access
- `SUPABASE_SERVICE_ROLE_KEY`: Admin database access

## Support

For issues or questions, please check the project documentation or contact support.
