# project-bottelegram
project-bottelegram
<?php 
error_reporting(E_ALL);
ini_set('display_errors', 1);
$Tokens = "my token telegram";
$Api_Url = "https://api.telegram.org/bot";
$Response = file_get_contents($Api_Url, "getUpdates?offset=-1");
$Updates = json_decode($Response, true);
foreach($Updates['result'] as $update)  {
    if(isset($update['message'])) {
        $chat_id = $update['message']['chat']['id'];
        $first_Name = isset($update['message']['chat']['id']) ? $update['message']['chat']['first_Name'] : "Users Name";
        $User_Name = isset($update['message']['chat']['User_Name']) ? $update['message']['chat']['User_Name'] : 'Username not set';
        $Massage = "👤 Username: $Message . 🆔 Chat ID:  . $chat_id";
        $Numbers = isset($update['message']['chat']['Numbers']) ? $update['message']['chat']['Numbers'] : 'number_admin';
        $Ip = $_SERVER['REMOTE_ADDR'];
        $Ip_Address = isset($update['message']['chat']['Address']) ? $update['message']['chat']['Address'] : 'ip_found';
        $Texts = $update['message']['Text'];
              switch($Texts) {
            case "/start" :
                sendTelegramMessage($chat_id, "Hello 💚 $first_Name" . "Welcome to bot telegram me");
                break;
                case "/ID" :
                    sendTelegramMessage($chat_id, "Hi" . $Message);
                    break;
                    case "/photos" :
                        sendPhotoByFile($chat_id, "image.jpg", "send to photo file server");
                        break;
                             case "/videos" :
                            sendVideoByFile($chat_id, "test.mp4", "send to video file server");
                            break;
                            case "/Music" :
                                sendAudibyFile($chat_id, "zendegi.mp3", "send to audio file server");
                                break;

                                default :
                                sendTelegramMessage($chat_id, "Not Found server!");
                                break;
        }
    }
}

                        // send function server
                        // =============================================================================================================****
                        function sendTelegramMessage($chat_id, $Massage)  {
                            global  $Tokens;
                            $Api_Url = "https://api.telegram.org/bot/sendMessage";
                            $Datas = [
                                'chat_id' => $chat_id,
                                'message' => $Message
                            ];
                        
                            $CH = curl_init($Api_Url);
                            curl_setopt($CH, CURLOPT_RETURNTRANSFER, true);
                            curl_setopt($CH, CURLOPT_POST, true);
                            curl_setopt($Ch, CURLOPT_POSTFIELDS, $Datas);
                            curl_exec($Ch);
                            curl_close($CH);
                        
                        }
                        // =============================================================================================================////

                        // send to function photos
                        // =============================================================================================================***
                        
                        function sendPhotoByFile($chat_id, $photo_path, $caption)  {
                            global $Tokens;
                            $Api_Url = "https://api.telegram.org/bot/sendMessage";
                            $Datas = [
                                'chat_id' => $chat_id ,
                                'photo' => new CRULFILE(realpath($photo_path)) ,
                                'caption' => $caption
                            ];
                        
                            $CH = curl_init($Api_Url);
                            curl_setopt($CH, CURLOPT_RETURNTRANSFER, true);
                            crul_setopt($CH, CRULOPT_POST, true);
                            crul_setopt($CH, CRULOPT_POSTFILEDS, $Datas);
                            curl_exec($CH);
                            curl_close($CH);
                        
                        }
                        
                        // =============================================================================================================////
                        
                        // send to function video 
                        // =============================================================================================================***

                                  function sendVideoByFile($chat_id, $video_path, $caption)  {
                              
                                  global $Tokens;
                                  $Api_Url = "https://api.telegram.org/bot/sendMessage";
                              
                                  $Datas = [
                                      'chat_id' => $chat_id,
                                      'video' => $video_path,
                                      'caption' => $caption
                                  ];
                              
                                  $CH = crul_init($Api_Url);
                                  crul_setopt($CH,  CURLOPT_RETURNTRANSFER, true);
                                  crul_setopt($CH, CRULOPT_POST, true);
                                  crul_setopt($CH, CRULOPT_POSTFILEDS, true);
                                  crul_exec($CH);
                                  crul_close($Ch);
                              }

                              // =============================================================================================================////
                        
                              // send to function music

                              // =============================================================================================================***

                                function sendAudioByFile($chat_id, $audio_path, $caption)   {
                                 
                                    global $Tokens;
                                    $Api_Url = "https://api.telegram.org/bot/sendMessage";
                                
                                    $Datas = [
                                        'chat_id' => $chat_id ,
                                        'audio_path' => $audio_path ,
                                        'caption' => $caption
                                    ];
                                
                                    $CH = curl_init($Api_Url);
                                    curl_setopt($CH, CRULOPT_RETURNTRANSFER, true);
                                    curl_setopt($CH, CRULOPT_POST, true);
                                    crul_setopt($CH, CRULOPT_POSTFILEDS, true);
                                    crul_exec($Ch);
                                    crul_close($CH);
                                }
                                
                                // =============================================================================================================////
                              
                              ?>
