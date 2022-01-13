# Unity snippets

### iOS build

__________________________________________________________________
If you get error "StackConsentManager.h file not found unity"
1. Open your podfile in your build folder
2. Add ``pod 'StackConsentManager', '~> 1.1.2'``
3. Run ``pod install`` in your build folder
__________________________________________________________________

Unity-Iphone -> Build Settings -> Always Embed Swift Standard Libraries -> Yes

UnityFramework -> Build Settings -> Always Embed Swift Standard Libraries -> No

__________________________________________________________________

Unity-Iphone -> (General tab) Frameworks, Libraries, Embedded content + "AuthenticationServices.framework"

__________________________________________________________________

#### If above doesn't work, try:

Unity-Iphone -> Build Phases -> + -> New Run Script Phase -> Add this script:

cd "${CONFIGURATION_BUILD_DIR}/${UNLOCALIZED_RESOURCES_FOLDER_PATH}/Frameworks/UnityFramework.framework/"
if [[ -d "Frameworks" ]]; then
    rm -fr Frameworks
fi

### Abdroid Facebook keystore path
C:\Users\YOUR_USER\.android\debug.keystore

### Monitor unity warnings, debug, errors

#### Open:
C:\Users\Ursa\AppData\Local\Android\Sdk\tools\monitor.bat

### how to manually install Android SDK target versions

#### Navigate to:
cd C:\Program Files\Unity\Hub\Editor\[UNITYVERSION]\Editor\Data\PlaybackEngines\AndroidPlayer\SDK\tools\bin

#### Run:
sdkmanager "platform-tools" "platforms;android-30"

### how to use logcat to receive messages from android device:

#### Navigate to:
C:\Users\USERNAME\AppData\Local\Android\sdk\platform-tools

#### Run command:
./adb logcat -s Unity PackageManager dalvikvm DEBUG > logcat.txt


# Git snippets

#### change git origin
git remote rm origin  
git remote add origin new_url.git  
git config master.remote origin  
git config master.merge refs/heads/master  

#### start ignoring commited file
git update-index --assume-unchanged <file>
  
#### stop ignoring commited file
git update-index --no-assume-unchanged <file>
  
#### stage all whole working tree, even with manually deleted files
git add -u :/

#### clear unstaged
git clean -df

# symfony_snippets with docker

#### make migrations, entities, controllers etc.

winpty docker-compose exec php-fpm php bin/console doctrine:migrations:diff  
winpty docker-compose exec php-fpm php bin/console make:{migration/entity/controller}

#### migrate

winpty docker-compose exec php-fpm php bin/console doctrine:migrations:migrate

#### drop database

winpty docker-compose exec php-fpm php bin/console doctrine:database:drop --force

#### create database

winpty docker-compose exec php-fpm php bin/console doctrine:database:create

#### load fixtures

winpty docker-compose exec php-fpm php bin/console doctrine:fixtures:load

#### flush database with entity structure

winpty docker-compose exec php-fpm php bin/console d:s:u --force

#### start symfony server

php bin/console server:run

#### show js routes

php bin/console fos:js-routing:dump

#### generate js json routes

php bin/console fos:js-routing:dump --format=json --target=assets/js/js_routes.json

#### after deploy
php bin/console cache:clear  
chmod -R 777 var/cache var/log



________________________________________________________________________________________________________________________________

# laravel snippets

#### link storage
php artisan storage:link

#### link storage manually
ln -sfn /var/www/source/public/ /var/www/source/public_html/storage

#### build assets
npm run dev
npm run production

___________________________________________________________________________________________________________________________________


# docker_snippets

#### list all container ids

docker ps -aq

#### stop all running containers

docker stop $(docker ps -aq)

#### remove all containers

docker rm $(docker ps -aq)

#### remove all images

docker rmi $(docker images -q)

#### list all volumes
docker volume ls

#### load fixtures
php bin/console doctrine:fixtures:load

#### composer install
docker-compose exec -u 1000 php-fpm composer install

___________________________________________________________________________________________________________________________________
# Vagrant snippets

#### reload
vagrant reload --provision

___________________________________________________________________________________________________________________________________

# PhpStorm snippets

For Windows Users:
go to C:\Windows\System32\drivers\etc\hosts
Add this line "0.0.0.0 account.jetbrains.com" (without quotes)

For Linux/Mac users:
Open /etc/hosts file. (go to terminal and type: sudo nano /etc/hosts)
Add this line "0.0.0.0 account.jetbrains.com" (without quotes)

Then restart phpstorm and paste the activation code:

2JA97R55MG-eyJsaWNlbnNlSWQiOiIySkE5N1I1NU1HIiwibGljZW5zZWVOYW1lIjoiWGlhbmdRaWFuIExpIiwiYXNzaWduZWVOYW1lIjoiIiwiYXNzaWduZWVFbWFpbCI6IiIsImxpY2Vuc2VSZXN0cmljdGlvbiI6IkZvciBlZHVjYXRpb25hbCB1c2Ugb25seSIsImNoZWNrQ29uY3VycmVudFVzZSI6ZmFsc2UsInByb2R1Y3RzIjpbeyJjb2RlIjoiSUkiLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifSx7ImNvZGUiOiJSUzAiLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifSx7ImNvZGUiOiJXUyIsInBhaWRVcFRvIjoiMjAxOS0wNS0xNSJ9LHsiY29kZSI6IlJEIiwicGFpZFVwVG8iOiIyMDE5LTA1LTE1In0seyJjb2RlIjoiUkMiLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifSx7ImNvZGUiOiJEQyIsInBhaWRVcFRvIjoiMjAxOS0wNS0xNSJ9LHsiY29kZSI6IkRCIiwicGFpZFVwVG8iOiIyMDE5LTA1LTE1In0seyJjb2RlIjoiUk0iLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifSx7ImNvZGUiOiJETSIsInBhaWRVcFRvIjoiMjAxOS0wNS0xNSJ9LHsiY29kZSI6IkFDIiwicGFpZFVwVG8iOiIyMDE5LTA1LTE1In0seyJjb2RlIjoiRFBOIiwicGFpZFVwVG8iOiIyMDE5LTA1LTE1In0seyJjb2RlIjoiR08iLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifSx7ImNvZGUiOiJQUyIsInBhaWRVcFRvIjoiMjAxOS0wNS0xNSJ9LHsiY29kZSI6IkNMIiwicGFpZFVwVG8iOiIyMDE5LTA1LTE1In0seyJjb2RlIjoiUEMiLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifSx7ImNvZGUiOiJSU1UiLCJwYWlkVXBUbyI6IjIwMTktMDUtMTUifV0sImhhc2giOiI5MDEzNjEyLzAiLCJncmFjZVBlcmlvZERheXMiOjAsImF1dG9Qcm9sb25nYXRlZCI6ZmFsc2UsImlzQXV0b1Byb2xvbmdhdGVkIjpmYWxzZX0=-QKv1wc5SQbR7KaOeDig4Qxs3ZKSkwEukdk4Fww0m5icI6WOBiRm7fZ9h15DXeZ5LlGBOI/EgGgomIv1/pHOBvSAt9SNV0/0ppnt35ULIc4Hk4Ji+DNRqejlmUJ730R+iJNdXiLOrsa/K6ULY34jRJLWNa/zcOakdb2sgoBcEnWFF5wL0IBgV+k8IWB+9cceZJv567PRQF0/SOt1aJy906PQ4+ro6PoqBHzndAuM40fFGpMY4hW58MCPtp6um4X9tJT3okNlNQm6z9VKRXxa7ANeiGZmWRIzks/FLhqEZ9gVLXSQzE/oyWBu+Pe6E0ohIvwlZIIsxdfTdA1TSpPmBpA==-MIIEPjCCAiagAwIBAgIBBTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE1MTEwMjA4MjE0OFoXDTE4MTEwMTA4MjE0OFowETEPMA0GA1UEAwwGcHJvZDN5MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxcQkq+zdxlR2mmRYBPzGbUNdMN6OaXiXzxIWtMEkrJMO/5oUfQJbLLuMSMK0QHFmaI37WShyxZcfRCidwXjot4zmNBKnlyHodDij/78TmVqFl8nOeD5+07B8VEaIu7c3E1N+e1doC6wht4I4+IEmtsPAdoaj5WCQVQbrI8KeT8M9VcBIWX7fD0fhexfg3ZRt0xqwMcXGNp3DdJHiO0rCdU+Itv7EmtnSVq9jBG1usMSFvMowR25mju2JcPFp1+I4ZI+FqgR8gyG8oiNDyNEoAbsR3lOpI7grUYSvkB/xVy/VoklPCK2h0f0GJxFjnye8NT1PAywoyl7RmiAVRE/EKwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQC9WZuYgQedSuOc5TOUSrRigMw4/+wuC5EtZBfvdl4HT/8vzMW/oUlIP4YCvA0XKyBaCJ2iX+ZCDKoPfiYXiaSiH+HxAPV6J79vvouxKrWg2XV6ShFtPLP+0gPdGq3x9R3+kJbmAm8w+FOdlWqAfJrLvpzMGNeDU14YGXiZ9bVzmIQbwrBA+c/F4tlK/DV07dsNExihqFoibnqDiVNTGombaU2dDup2gwKdL81ua8EIcGNExHe82kjF4zwfadHk3bQVvbfdAwxcDy4xBjs3L4raPLU3yenSzr/OEur1+jfOxnQSmEcMXKXgrAQ9U55gwjcOFKrgOxEdek/Sk1VfOjvS+nuM4eyEruFMfaZHzoQiuw4IqgGc45ohFH0UUyjYcuFxxDSU9lMCv8qdHKm+wnPRb0l9l5vXsCBDuhAGYD6ss+Ga+aDY6f/qXZuUCEUOH3QUNbbCUlviSz6+GiRnt1kA9N2Qachl+2yBfaqUqr8h7Z2gsx5LcIf5kYNsqJ0GavXTVyWh7PYiKX4bs354ZQLUwwa/cG++2+wNWP+HtBhVxMRNTdVhSm38AknZlD+PTAsWGu9GyLmhti2EnVwGybSD2Dxmhxk3IPCkhKAK+pl0eWYGZWG3tJ9mZ7SowcXLWDFAk0lRJnKGFMTggrWjV8GYpw5bq23VmIqqDLgkNzuoog==
