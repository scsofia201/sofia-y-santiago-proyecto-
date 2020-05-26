# sofia-y-santiago-proyecto-
(require (lib "graphics.ss" "graphics"))
(open-graphics)

 
 
(define ventana (open-viewport "pokemon" 600 500))


;(((draw-pixmap-posn "mapa 1 a.jpg" 'unknown/mask ) ventana) (make-posn 0 0))

(define (fondooak)
(begin
((draw-viewport ventana) (make-rgb 0.6 0.850922 0.917))
(((draw-pixmap-posn "profesor oak.png" 'unknown/mask ) ventana) (make-posn 175 0)) (sleep 1)
(((draw-pixmap-posn "nueve1.png" 'unknown/mask ) ventana) (make-posn 0 300))
  ))

(define (dialogo-oak cont)
 (if (equal? (key-value (get-key-press ventana)) (integer->char 13))
                        
  (begin ((draw-viewport ventana) "white")
  (if (>= 3 cont)
      (begin (fondooak)
             (cond
               ((= cont 1)
                (begin
                  (sleep 2) ((draw-string ventana) (make-posn 50 350) "¡Hola a todos! ¡Bienvenidos al mundo de POKÉMON! ¡Me llamo OAK! ¡Pero la gente me llama el" "black")
                  (sleep 2) ((draw-string ventana) (make-posn 50 370) "PROFESOR POKÉMON! ¡Este mundo está habitado por unas criaturas llamadas POKÉMON! Para" "black")
                  (sleep 2) ((draw-string ventana) (make-posn 50 390) "algunos, los POKÉMON son mascotas. Pero otros los usan para pelear." "black")
                     (dialogo-oak (+ cont 1))))

               ((= cont 2)
                (begin
                  (sleep 2) ((draw-string ventana) (make-posn 50 350) "En cuanto a mí... Estudio a los POKÉMON como profesión. Pero primero dime" "black")
                  (sleep 2) ((draw-string ventana) (make-posn 50 370) "como te llamas. (...) ¡Bien! ¡Tu nombre es:" "black")
                  (sleep 2) ((draw-string ventana) (make-posn 50 390) "espacio nombre." "black")
                     (dialogo-oak (+ cont 1))))

               ((= cont 3)
                (begin
                  (sleep 2)((draw-string ventana) (make-posn 50 350) "¡Tu propia leyenda POKÉMON está a punto de comenzar!" "black")
                  (sleep 2)((draw-string ventana) (make-posn 50 370) "¡Te espera un mundo de sueños y aventuras con los POKÉMON!" "black")
                  (sleep 2)((draw-string ventana) (make-posn 50 390) "¡Adelante!" "black")
                     
                        (dialogo-oak (+ cont 1))) (dialogo-oak cont)))
               )))(dialogo-oak cont)) )


 (dialogo-oak 1)
