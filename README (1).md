# iSTG-website
import React, { useState } from 'react';
import { 
  Settings as SettingsIcon, 
  Shield, 
  Bell, 
  User, 
  Lock, 
  Eye, 
  Moon, 
  Sun, 
  Globe,
  Smartphone,
  Mail,
  Heart,
  Save,
  AlertTriangle,
  Download,
  Trash2
} from 'lucide-react';

const Settings = () => {
  const [activeTab, setActiveTab] = useState('privacy');
  const [settings, setSettings] = useState({
    // Privacy Settings
    anonymousMode: true,
    showOnlineStatus: false,
    allowDirectMessages: false,
    dataCollection: 'minimal',
    
    // Notification Settings
    emailNotifications: true,
    commentNotifications: true,
    likeNotifications: false,
    weeklyDigest: true,
    safetyAlerts: true,
    
    // Appearance Settings
    darkMode: false,
    language: 'en',
    fontSize: 'medium',
    animationsEnabled: true,
    
    // Account Settings
    twoFactorAuth: false,
    sessionTimeout: '30',
    autoLogout: true,
  });

  const tabs = [
    { id: 'privacy', label: 'Privacy & Safety', icon: Shield },
    { id: 'notifications', label: 'Notifications', icon: Bell },
    { id: 'appearance', label: 'Appearance', icon: Eye },
    { id: 'account', label: 'Account Security', icon: Lock },
  ];

  const handleSettingChange = (category: string, setting: string, value: any) => {
    setSettings(prev => ({
      ...prev,
      [setting]: value
    }));
  };

  const saveSettings = () => {
    // Handle settings save
    console.log('Saving settings:', settings);
  };

  const exportData = () => {
    // Handle data export
    console.log('Exporting user data');
  };

  const deleteAccount = () => {
    // Handle account deletion
    if (confirm('Are you sure you want to delete your account? This action cannot be undone.')) {
      console.log('Deleting account');
    }
  };

  return (
    <div className="min-h-screen py-8 px-4 sm:px-6 lg:px-8">
      <div className="max-w-4xl mx-auto">
        {/* Header */}
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold text-white mb-4">
            <span className="bg-gradient-to-r from-pink-400 to-purple-400 bg-clip-text text-transparent">
              Settings
            </span>
          </h1>
          <p className="text-white/80">
            Customize your anonymous experience and privacy controls
          </p>
        </div>

        <div className="grid lg:grid-cols-4 gap-8">
          {/* Sidebar Navigation */}
          <div className="lg:col-span-1">
            <nav className="glass rounded-2xl p-4 border border-white/20 sticky top-8">
              <div className="space-y-2">
                {tabs.map((tab) => {
                  const Icon = tab.icon;
                  return (
                    <button
                      key={tab.id}
                      onClick={() => setActiveTab(tab.id)}
                      className={`w-full flex items-center space-x-3 p-3 rounded-lg transition-all duration-200 ${
                        activeTab === tab.id
                          ? 'bg-white/20 text-white'
                          : 'text-white/70 hover:text-white hover:bg-white/10'
                      }`}
                    >
                      <Icon size={18} />
                      <span className="text-sm font-medium">{tab.label}</span>
                    </button>
                  );
                })}
              </div>
            </nav>
          </div>

          {/* Main Content */}
          <div className="lg:col-span-3">
            <div className="vintage-paper rounded-3xl p-8 transform -rotate-1 hover:rotate-0 transition-transform duration-300">
              
              {/* Privacy & Safety Tab */}
              {activeTab === 'privacy' && (
                <div>
                  <h2 className="text-2xl font-bold text-gray-800 mb-6 flex items-center">
                    <Shield className="mr-3 text-green-600" size={28} />
                    Privacy & Safety Settings
                  </h2>
                  
                  <div className="space-y-6">
                    <div className="bg-green-50 border border-green-200 rounded-lg p-4 mb-6">
                      <div className="flex items-start space-x-3">
                        <Shield className="text-green-600 mt-1" size={20} />
                        <div>
                          <h3 className="font-bold text-green-800">Your Privacy is Protected</h3>
                          <p className="text-green-700 text-sm mt-1">
                            These settings ensure your identity remains anonymous while using iStG.
                          </p>
                        </div>
                      </div>
                    </div>

                    <div className="grid gap-6">
                      <div className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                        <div>
                          <h4 className="font-bold text-gray-800">Anonymous Mode</h4>
                          <p className="text-gray-600 text-sm">Keep your identity completely hidden</p>
                        </div>
                        <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                          settings.anonymousMode ? 'bg-green-500' : 'bg-gray-300'
                        }`}>
                          <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                            settings.anonymousMode ? 'translate-x-6' : 'translate-x-0'
                          }`}></div>
                        </div>
                      </div>

                      <div className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                        <div>
                          <h4 className="font-bold text-gray-800">Show Online Status</h4>
                          <p className="text-gray-600 text-sm">Let others see when you're active</p>
                        </div>
                        <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                          settings.showOnlineStatus ? 'bg-blue-500' : 'bg-gray-300'
                        }`}>
                          <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                            settings.showOnlineStatus ? 'translate-x-6' : 'translate-x-0'
                          }`}></div>
                        </div>
                      </div>

                      <div className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                        <div>
                          <h4 className="font-bold text-gray-800">Allow Direct Messages</h4>
                          <p className="text-gray-600 text-sm">Receive anonymous messages from other users</p>
                        </div>
                        <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                          settings.allowDirectMessages ? 'bg-purple-500' : 'bg-gray-300'
                        }`}>
                          <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                            settings.allowDirectMessages ? 'translate-x-6' : 'translate-x-0'
                          }`}></div>
                        </div>
                      </div>

                      <div className="p-4 bg-white rounded-lg border border-gray-200">
                        <h4 className="font-bold text-gray-800 mb-2">Data Collection Level</h4>
                        <p className="text-gray-600 text-sm mb-3">Choose how much data we collect to improve your experience</p>
                        <div className="space-y-2">
                          {[
                            { value: 'minimal', label: 'Minimal', desc: 'Only essential data for functionality' },
                            { value: 'standard', label: 'Standard', desc: 'Basic analytics to improve the platform' },
                            { value: 'enhanced', label: 'Enhanced', desc: 'Full analytics for personalized experience' }
                          ].map((option) => (
                            <label key={option.value} className="flex items-start space-x-3 cursor-pointer">
                              <input
                                type="radio"
                                name="dataCollection"
                                value={option.value}
                                checked={settings.dataCollection === option.value}
                                onChange={(e) => handleSettingChange('privacy', 'dataCollection', e.target.value)}
                                className="mt-1 w-4 h-4 text-purple-600"
                              />
                              <div>
                                <span className="font-medium text-gray-800">{option.label}</span>
                                <p className="text-xs text-gray-600">{option.desc}</p>
                              </div>
                            </label>
                          ))}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              )}

              {/* Notifications Tab */}
              {activeTab === 'notifications' && (
                <div>
                  <h2 className="text-2xl font-bold text-gray-800 mb-6 flex items-center">
                    <Bell className="mr-3 text-blue-600" size={28} />
                    Notification Preferences
                  </h2>
                  
                  <div className="space-y-6">
                    {[
                      { key: 'emailNotifications', icon: Mail, title: 'Email Notifications', desc: 'Receive updates via email' },
                      { key: 'commentNotifications', icon: Bell, title: 'Comment Notifications', desc: 'When someone comments on your posts' },
                      { key: 'likeNotifications', icon: Heart, title: 'Like Notifications', desc: 'When someone likes your confessions' },
                      { key: 'weeklyDigest', icon: Globe, title: 'Weekly Digest', desc: 'Summary of community activity' },
                      { key: 'safetyAlerts', icon: AlertTriangle, title: 'Safety Alerts', desc: 'Important security and safety updates' }
                    ].map((notification) => {
                      const Icon = notification.icon;
                      return (
                        <div key={notification.key} className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                          <div className="flex items-center space-x-3">
                            <Icon className="text-gray-600" size={20} />
                            <div>
                              <h4 className="font-bold text-gray-800">{notification.title}</h4>
                              <p className="text-gray-600 text-sm">{notification.desc}</p>
                            </div>
                          </div>
                          <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                            settings[notification.key as keyof typeof settings] ? 'bg-blue-500' : 'bg-gray-300'
                          }`}>
                            <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                              settings[notification.key as keyof typeof settings] ? 'translate-x-6' : 'translate-x-0'
                            }`}></div>
                          </div>
                        </div>
                      );
                    })}
                  </div>
                </div>
              )}

              {/* Appearance Tab */}
              {activeTab === 'appearance' && (
                <div>
                  <h2 className="text-2xl font-bold text-gray-800 mb-6 flex items-center">
                    <Eye className="mr-3 text-purple-600" size={28} />
                    Appearance Settings
                  </h2>
                  
                  <div className="space-y-6">
                    <div className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                      <div className="flex items-center space-x-3">
                        {settings.darkMode ? <Moon className="text-gray-600" size={20} /> : <Sun className="text-yellow-600" size={20} />}
                        <div>
                          <h4 className="font-bold text-gray-800">Dark Mode</h4>
                          <p className="text-gray-600 text-sm">Switch to dark theme</p>
                        </div>
                      </div>
                      <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                        settings.darkMode ? 'bg-gray-800' : 'bg-yellow-400'
                      }`}>
                        <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                          settings.darkMode ? 'translate-x-6' : 'translate-x-0'
                        }`}></div>
                      </div>
                    </div>

                    <div className="p-4 bg-white rounded-lg border border-gray-200">
                      <h4 className="font-bold text-gray-800 mb-3 flex items-center">
                        <Globe className="mr-2" size={20} />
                        Language
                      </h4>
                      <select
                        value={settings.language}
                        onChange={(e) => handleSettingChange('appearance', 'language', e.target.value)}
                        className="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-500"
                      >
                        <option value="en">English</option>
                        <option value="es">Español</option>
                        <option value="fr">Français</option>
                        <option value="de">Deutsch</option>
                      </select>
                    </div>

                    <div className="p-4 bg-white rounded-lg border border-gray-200">
                      <h4 className="font-bold text-gray-800 mb-3">Font Size</h4>
                      <div className="flex space-x-4">
                        {['small', 'medium', 'large'].map((size) => (
                          <button
                            key={size}
                            onClick={() => handleSettingChange('appearance', 'fontSize', size)}
                            className={`px-4 py-2 rounded-lg border transition-all duration-200 ${
                              settings.fontSize === size
                                ? 'border-purple-500 bg-purple-50 text-purple-700'
                                : 'border-gray-300 hover:border-purple-300'
                            }`}
                          >
                            {size.charAt(0).toUpperCase() + size.slice(1)}
                          </button>
                        ))}
                      </div>
                    </div>
                  </div>
                </div>
              )}

              {/* Account Security Tab */}
              {activeTab === 'account' && (
                <div>
                  <h2 className="text-2xl font-bold text-gray-800 mb-6 flex items-center">
                    <Lock className="mr-3 text-red-600" size={28} />
                    Account Security
                  </h2>
                  
                  <div className="space-y-6">
                    <div className="bg-red-50 border border-red-200 rounded-lg p-4 mb-6">
                      <div className="flex items-start space-x-3">
                        <AlertTriangle className="text-red-600 mt-1" size={20} />
                        <div>
                          <h3 className="font-bold text-red-800">Account Security Settings</h3>
                          <p className="text-red-700 text-sm mt-1">
                            These settings help protect your anonymous account from unauthorized access.
                          </p>
                        </div>
                      </div>
                    </div>

                    <div className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                      <div>
                        <h4 className="font-bold text-gray-800">Two-Factor Authentication</h4>
                        <p className="text-gray-600 text-sm">Add an extra layer of security</p>
                      </div>
                      <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                        settings.twoFactorAuth ? 'bg-green-500' : 'bg-gray-300'
                      }`}>
                        <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                          settings.twoFactorAuth ? 'translate-x-6' : 'translate-x-0'
                        }`}></div>
                      </div>
                    </div>

                    <div className="p-4 bg-white rounded-lg border border-gray-200">
                      <h4 className="font-bold text-gray-800 mb-3">Session Timeout</h4>
                      <select
                        value={settings.sessionTimeout}
                        onChange={(e) => handleSettingChange('account', 'sessionTimeout', e.target.value)}
                        className="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-500"
                      >
                        <option value="15">15 minutes</option>
                        <option value="30">30 minutes</option>
                        <option value="60">1 hour</option>
                        <option value="240">4 hours</option>
                      </select>
                    </div>

                    <div className="flex items-center justify-between p-4 bg-white rounded-lg border border-gray-200">
                      <div>
                        <h4 className="font-bold text-gray-800">Auto Logout</h4>
                        <p className="text-gray-600 text-sm">Automatically log out when inactive</p>
                      </div>
                      <div className={`w-12 h-6 rounded-full p-1 transition-colors duration-200 ${
                        settings.autoLogout ? 'bg-orange-500' : 'bg-gray-300'
                      }`}>
                        <div className={`w-4 h-4 bg-white rounded-full transition-transform duration-200 ${
                          settings.autoLogout ? 'translate-x-6' : 'translate-x-0'
                        }`}></div>
                      </div>
                    </div>
                  </div>

                  {/* Danger Zone */}
                  <div className="mt-8 p-6 bg-red-50 border-2 border-red-200 rounded-lg">
                    <h3 className="text-lg font-bold text-red-800 mb-4 flex items-center">
                      <AlertTriangle className="mr-2" size={20} />
                      Danger Zone
                    </h3>
                    <div className="space-y-4">
                      <button
                        onClick={exportData}
                        className="w-full flex items-center justify-center space-x-2 p-3 bg-blue-600 hover:bg-blue-700 text-white rounded-lg transition-colors duration-200"
                      >
                        <Download size={18} />
                        <span>Export My Data</span>
                      </button>
                      <button
                        onClick={deleteAccount}
                        className="w-full flex items-center justify-center space-x-2 p-3 bg-red-600 hover:bg-red-700 text-white rounded-lg transition-colors duration-200"
                      >
                        <Trash2 size={18} />
                        <span>Delete Account</span>
                      </button>
                    </div>
                  </div>
                </div>
              )}

              {/* Save Button */}
              <div className="mt-8 pt-6 border-t border-gray-200">
                <button
                  onClick={saveSettings}
                  className="w-full cute-button rounded-lg py-3 font-bold flex items-center justify-center space-x-2"
                >
                  <Save size={20} />
                  <span>Save All Settings</span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default Settings;
