source "https://github.com/BendingSpoons/kss-cocoapods"
source 'https://github.com/CocoaPods/Specs.git'

inhibit_all_warnings!
use_frameworks!

target 'Tempura' do
  platform :ios, '9.0'
  podspec

  target 'TempuraTests' do
    inherit! :search_paths
    pod 'Quick'
    pod 'Nimble'
  end

  target 'Demo' do
    pod 'Tempura', :path => './'
    pod 'PinLayout'
    pod 'BonMot'
    pod 'Hero'
    pod 'Chocolate'
  end
end


post_install do |installer|
  # Your list of targets here.
  legacyTargets = ['BonMot', 'Hero']
  
  installer.pods_project.targets.each do |target|
    if legacyTargets.include? target.name
      target.build_configurations.each do |config|
        config.build_settings['SWIFT_VERSION'] = '3.2'
      end
    end
    if target.name == 'Tempura'
      target.build_configurations.each do |config|
        if config.name == 'Debug'
          config.build_settings['OTHER_SWIFT_FLAGS'] = '-DDEBUG'
        else
          config.build_settings['OTHER_SWIFT_FLAGS'] = ''
        end
      end
    end
  end
end
