# sofia-y-santiago-proyecto-
(require (lib "graphics.ss" "graphics"))
(open-graphics)

(define (fondooak ventana)
  (begin
    ((draw-viewport ventana) (make-rgb 0.6 0.850922 0.917))
    (((draw-pixmap-posn "profesor oak.png" 'unknown/mask ) ventana) (make-posn 175 0)) (sleep 1)
    (((draw-pixmap-posn "nueve1.png" 'unknown/mask ) ventana) (make-posn 0 300))
    ))

(define (dialogo-oak cont nombre ventana)
  (if (equal? (key-value (get-key-press ventana)) (integer->char 13))
      
      (begin ((draw-viewport ventana) "white")
          (if (>= 3 cont)
                 (begin (fondooak ventana)
                      (cond
                          ((= cont 1)
                           (begin
                             (sleep 2) ((draw-string ventana) (make-posn 50 330) "¡Hola a todos! ¡Bienvenidos al mundo de POKÉMON! ¡Me llamo OAK!" "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 355) "¡Pero la gente me llama el PROFESOR POKÉMON! ¡Este mundo " "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 380) "está habitado por unas criaturas llamadas POKÉMON! Para algunos," "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 405) " los POKÉMON son mascotas. Pero otros los usan para pelear." "black")
                             (dialogo-oak (+ cont 1) nombre ventana)))

                          ((= cont 2)
                           (begin
                             (sleep 2) ((draw-string ventana) (make-posn 50 350) "En cuanto a mí... Estudio a los POKÉMON como profesión." "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 370) "Asi que tu nombre es:" "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 390) nombre "black")
                             (dialogo-oak (+ cont 1) nombre ventana)))

                          ((= cont 3)
                           (begin
                             (sleep 2)((draw-string ventana) (make-posn 50 350) "¡Tu propia leyenda POKÉMON está a punto de comenzar!" "black")
                             (sleep 2)((draw-string ventana) (make-posn 50 370) "¡Te espera un mundo de sueños y aventuras con los POKÉMON!" "black")
                             (sleep 2)((draw-string ventana) (make-posn 50 390) "¡Adelante!" "black")
                             (dialogo-oak (+ cont 1) nombre ventana)))))
                 )) (dialogo-oak cont nombre ventana)) )
                 
    (define (principal)
    (begin  
    (displayln "bienvenido a pokemon, por favor ingrese el nombre del jugador (no olvide ponerlo entre comillas)")
    (define nombre (read))
    (newline)
    (displayln "por favor indique su genero (1/hombre 2/mujer) ")
    (define sexo (read))
    (define ventana (open-viewport "pokemon" 600 500))
    ((draw-pixmap ventana) "portada inicio.jpg" (make-posn 0 0) "blue")
    (dialogo-oak 1 nombre ventana)
    )) (principal)

