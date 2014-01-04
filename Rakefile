DESTINATIONS = ["name=iPhone Retina (3.5-inch),OS=7.0",
                "name=iPhone Retina (4-inch),OS=7.0",
                "name=iPhone Retina (4-inch 64-bit),OS=7.0"]

task :default => [:build, :clean, :test]

desc "build"
task :build, :workspace, :schemes do |t, args|
  schemes = args[:schemes].gsub(/'/, '').split(' ')
  schemes.each do |scheme|
    system("xcodebuild -workspace #{args[:workspace]} -scheme #{scheme}")
  end
end

desc "clean"
task :clean, :workspace, :schemes do |t, args|
  schemes = args[:schemes].gsub(/'/, '').split(' ')
  schemes.each do |scheme|
    system("xcodebuild clean -workspace #{args[:workspace]} -scheme #{scheme} | xcpretty -c")
  end
end

desc "run unit tests"
task :test, :workspace, :schemes do |t, args|
  schemes = args[:schemes].gsub(/'/, '').split(' ')
  schemes.each do |scheme|
    DESTINATIONS.each do |destination|
      system("xcodebuild test -workspace #{args[:workspace]} -scheme #{scheme} -configuration Debug -sdk iphonesimulator -destination \"#{destination}\" | xcpretty -c")
    end
  end
end
