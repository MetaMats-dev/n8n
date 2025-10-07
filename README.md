# Content Pipeline Workflows - Setup Guide

## 📁 Files Created

1. **`ai_processing_workflow.json`** - Enhanced AI processing workflow
2. **`ghost_publishing_workflow.json`** - Enhanced Ghost publishing workflow  
3. **`error_handler_workflow.json`** - Centralized error handling workflow

## 🔧 Environment Variables Required

Set these in your n8n instance:

```bash
NOTION_CONTENT_DB_ID=your_notion_database_id
NOTION_ERROR_LOG_DB_ID=your_error_log_database_id
GHOST_URL=https://your-ghost-site.com
GHOST_ADMIN_API_KEY=your_ghost_admin_api_key
OPENAI_API_KEY=your_openai_api_key
WEBHOOK_URL=your_webhook_url_for_notifications
SLACK_WEBHOOK_URL=your_slack_webhook_url
```

## 📋 Notion Database Setup

### Content Database Properties:
- **Titel** (Title) - Main content title
- **Inhoud (Body)** (Rich Text) - Original content
- **AI Output** (Rich Text) - AI processed content
- **AI Review** (Checkbox) - Review status
- **Status** (Select) - In Progress, Ready, Published, Error
- **Categorie** (Multi-select) - Content categories
- **Tool** (Select) - Tool/technology tags
- **Samenvatting (Excerpt)** (Rich Text) - Content summary
- **Publicatie-URL** (URL) - Published article URL
- **Ghost Post ID** (Rich Text) - Ghost post identifier
- **Error Message** (Rich Text) - Error details
- **Processing Date** (Date) - When processed
- **Publish Date** (Date) - When published
- **Featured Image** (Files) - Article featured image

### Error Log Database Properties:
- **Workflow Name** (Title) - Which workflow failed
- **Error Message** (Rich Text) - Error details
- **Execution ID** (Rich Text) - n8n execution ID
- **Timestamp** (Date) - When error occurred
- **Status** (Select) - New, Investigating, Resolved

## 🚀 Import Instructions

1. **Import Workflows**: Import each JSON file into n8n
2. **Configure Credentials**: Set up OpenAI, Notion, and Ghost API credentials
3. **Set Environment Variables**: Add all required env vars
4. **Test Workflows**: Run test executions with sample data
5. **Set Up Monitoring**: Configure webhook notifications

## ✨ Key Improvements Made

### Error Handling
- ✅ Comprehensive validation at each step
- ✅ Retry mechanisms for API failures
- ✅ Clear error states and messages
- ✅ Centralized error logging

### Security
- ✅ Environment variables for sensitive data
- ✅ HTML escaping to prevent XSS
- ✅ Proper credential management

### Performance
- ✅ Timeout settings for API calls
- ✅ Efficient data processing
- ✅ Optimized workflow structure

### Monitoring
- ✅ Real-time notifications
- ✅ Error tracking in Notion
- ✅ Success/failure webhooks

## 🔄 Workflow Flow

1. **AI Processing**: Notion → Validation → AI → Validation → Notion
2. **Ghost Publishing**: Notion → Validation → Ghost → Notion → Notifications
3. **Error Handling**: Webhook → Slack + Notion logging

## 🛠️ Customization

- Modify AI prompts in the OpenAI node
- Adjust validation rules in IF nodes
- Customize notification messages
- Add additional error handling paths

## 📞 Support

For issues or questions about these workflows, check the error logs in Notion or Slack notifications.
