# Multiverse Viewer v6.0 - Changelog

## Major Improvements & Fixes

### 🎨 Enhanced Customization & Settings
- **Renamed "Developer Tools" to "Settings"** - More user-friendly terminology
- **Added new settings options**:
  - "Show other nodes (purple)" - Toggle visibility of non-standard role nodes (non-user, non-assistant, non-system)
  - Consolidated all settings in one intuitive menu
- **Improved metadata toggle**:
  - Added "Hide Info"/"Show Info" button in viewer panel
  - Toggle displays/hides role badges, timestamps, and IDs
  - Saves preference between sessions via localStorage

### 🌿 Enhanced Branch Conversation View
- **Settings-aware filtering**: Branch views now respect system/other node visibility settings
- **Dynamic message counts**: Conversation summary shows filtered vs. total messages
- **Improved message copy functionality**:
  - Individual copy buttons for each message in branch view
  - Better handling of code blocks within messages
- **Enhanced visual feedback** when jumping to messages

### 🔧 Performance & Usability Improvements
- **Settings persistence**: All customization preferences saved locally
- **Node visibility management**: Proper handling of "other" nodes (purple circles)
- **Responsive design improvements**: Better handling of panel resizing and text positioning
- **Code cleanup**: Consolidated duplicate code and improved function organization

### 🎯 Enhanced Node Display Logic
- **Refined node filtering system**: Clear separation between:
  - System nodes (dashed circles, role: system)
  - User nodes (blue circles, role: user) 
  - Assistant nodes (green circles, role: assistant)
  - Other nodes (purple circles, non-standard roles)
- **Consistent visual treatment** across graph and branch views
- **Improved text positioning** to prevent overlaps

### 📊 Improved Conversation Summary
- **Detailed breakdown** of message types in branch view
- **Filtering information**: Shows how many messages are hidden by current settings
- **Visual statistics** with color-coded counts for each role type
- **Timestamp display** when metadata is enabled

### 🛠️ Technical Improvements
- **Consolidated initialization** into organized functions
- **Improved error handling** for format detection
- **Better localStorage management** for user preferences
- **Enhanced tooltip system** with proper copy functionality
- **Optimized tree rendering** for better performance

### 🐛 Bug Fixes
- **Fixed node visibility** when toggling "Show other nodes" setting
- **Corrected branch indexing** with filtered nodes
- **Improved search functionality** across conversations
- **Fixed PDF generation** for branch conversations
- **Enhanced drag-and-drop** file loading experience

### 📋 User Interface Polish
- **Consistent terminology** throughout the application
- **Improved button labels** and tooltips
- **Better visual hierarchy** in settings menu
- **Enhanced help system** with detailed topics
- **Streamlined workflow** for switching between conversations

### 🔄 Format Support Enhancements
- **Improved DeepSeek exporter** format detection
- **Better handling** of mixed conversation arrays
- **Enhanced Claude/Anthropic** format parsing
- **Robust error messages** for unsupported formats

## Key Changes Summary

1. **Settings Reorganization**: Consolidated all customization options into one intuitive menu
2. **Node Visibility Control**: Fine-grained control over different node types
3. **Branch View Improvements**: Settings-aware filtering and enhanced UI
4. **Metadata Management**: Toggle for showing/hiding technical information
5. **Performance Optimizations**: Better handling of large conversations
6. **User Experience Polish**: Streamlined workflows and clearer terminology

The update focuses on making the tool more customizable and user-friendly while maintaining all existing functionality for visualizing conversation trees across multiple AI platforms.
