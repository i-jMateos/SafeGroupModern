# Uncomment the next line to define a global platform for your project
platform :ios, '12.0'

target 'SafeGroup' do
  use_frameworks!

  pod 'Firebase/Analytics'
  pod 'Firebase/Auth'
  pod 'Firebase/Core'
  pod 'Firebase/Firestore'
  pod 'Firebase/Storage'
  pod 'Kingfisher'
  # pod 'p2pkit'
  pod 'ForceDirectedScene'
  pod 'FirebaseFirestoreSwift'
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '12.0'
      config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= ['$(inherited)']

      if target.name == 'BoringSSL-GRPC'
        target.source_build_phase.files.each do |file|
          if file.settings && file.settings['COMPILER_FLAGS']
            flags = file.settings['COMPILER_FLAGS'].split
            flags.reject! { |flag| flag == '-GCC_WARN_INHIBIT_ALL_WARNINGS' || flag == '-G' }
            file.settings['COMPILER_FLAGS'] = flags.join(' ')
          end
        end
      end
    end
  end
end
