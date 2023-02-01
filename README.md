# RocketGame

Hello everyone! I believe learn by doing is the most efficient way to get the concept,
I built this rocket game using jQuery to make it dynamic, have fun playing with it!
There are some technical details provided as following:

Main function:<br> 
1. move right and and left:<br>
function left_click_action() , function right_click_action(e)<br>
2. Initial position:<br> #stage{position:relative;} , .sprite{position:absolute;}<br>
3. Create Obstacle:<br> 
function create_enemy()
 - add enemy:<br> $stage.append
 - find last tag:<br> $stage.find(“.enemy:last”)
 - store wave value:<br> $enemy.data(“wave",enemy_wave);
 - (random position) array:<br>
                      var enemy_pos=[10,110,210];
                      var random_index = getRandomInt(0,enemy_pos.length-1);
                      var enemy_x = enemy_pos.splice(random_index,1)[0];
                          .splice(specific index, remove item number)

                   
                   
Game Initialization:<br>
1. return to original value: score, score_add, enemy_fallspeed, enemy_wave<br> 
2. Reset:player initial position, score initial position<br> 
3. create enemy, reset clock, player control<br>

Loop:<br>
Set function loop_func()<br>	
1. control each enemy:<br> $stage.find(“.enemy”).each(function()<br>
2. create enemies according to distance:<br>
               Store value:  $enemy.data(“wave”,enemy_wave)
               if(enemy_y>enemy_wave_gap && $(this).data("wave")==enemy_wave){
                            enemy_wave++;
                            create_enemy();
                        }<br>
3. Collision:<br>
- Set coordinate of the centre
- Collision: if(hit_r>pe_distance){
                            endgame();        
                        } 
- Score Increase: score+=score_add 
- Show on the screen: $score.html(score)
- Set in the front: z-index:order number<br>
          4.Remove from screen:<br>
                  if(enemy_y>$stage.height()){
                            $(this).remove();
                            return;
                        }<br>
                        
Speedup:<br>
1. function speed_func()<br>
2. set max speed<br>
               if(enemy_fallspeed>=enemy_max_fallspeed){
                        enemy_fallspeed=11;
                        clearInterval(speedup);
                    }<br> 
3. when speedup score added more<br> 
                enemy_fallspeed+=0.1;
                score_add+=1.1;


End Game:<br>
1. lock player<br> 
$body.unbind("click"); 
$body.unbind(“contextmenu");<br>
2. clear clock<br>
clearInterval(fall_loop);
clearInterval(speedup);<br>
3. Showing image of retry<br>
$stage.append("<div id=‘gameover'>RETRY</div>");
  
Audio:<br> 
1. Add audio:<br> <audio id="myAudio" src="DISS.mp3" muted></audio>
2. Add sound function:<br>
                 function sound_action(){                  
                    aud.play();
                    aud.muted=false;<br>
3. Init sound:<br> $body.mousedown(sound_action);<br>
4. End game the sound stopped:<br> $body.unbind(“mousedown");<br>
5. Click retry the sound reload and play:<br>
                  aud.load();
                  sound_action()
  

  
