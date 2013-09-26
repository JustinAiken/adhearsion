ENV['SKIP_RCOV'] = 'true'

group 'rspec' do
  guard 'rspec', :cli => '--format documentation' do
    watch(%r{^spec/.+_spec\.rb$})
    watch(%r{^lib/(.+)\.rb$})     { |m| "spec/#{m[1]}_spec.rb" }
    watch('spec/spec_helper.rb')  { "spec/" }
  end
end

group 'cucumber' do
  guard 'cucumber', :cli => '--profile guard', all_on_start: false do
    watch(%r{^features/.+\.feature$})
    watch(%r{^features/support/.+$})                      { 'features' }
    watch(%r{^features/step_definitions/(.+)_steps\.rb$}) { |m| Dir[File.join("**/#{m[1]}.feature")][0] || 'features' }
  end
end

guard 'yard' do
  watch(%r{lib/.+\.rb})
end
