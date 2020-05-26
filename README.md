# sofia-y-santiago-proyecto-
proyecto fina
(require (lib "graphics.ss" "graphics"))
(open-graphics)

(displayln "bienvenido a pokemon, por favor ingrese el nombre del jugador (no olvide ponerlo entre comillas)")
(define nombre (read))
(newline)
(displayln "por favor indique su genero (1/hombre 2/mujer) ")
(define sexo (read))


(define ventana (open-viewport "pokemon" 600 500))

;(((draw-pixmap-posn "mapa 1 a.jpg" 'unknown/mask ) ventana) (make-posn 0 0))

(define (fondooak)
  (begin
    ((draw-viewport ventana) (make-rgb 0.6 0.850922 0.917))
    (((draw-pixmap-posn "profesor oak.png" 'unknown/mask ) ventana) (make-posn 175 0)) (sleep 1)
    (((draw-pixmap-posn "nueve1.png" 'unknown/mask ) ventana) (make-posn 0 300))
    ))

(define (dialogo-oak cont nombre)
  (if (equal? (key-value (get-key-press ventana)) (integer->char 13))
                        
      (begin ((draw-viewport ventana) "white")
             (if (>= 3 cont)
                 (begin (fondooak)
                        (cond
                          ((= cont 1)
                           (begin
                             (sleep 2) ((draw-string ventana) (make-posn 50 330) "¡Hola a todos! ¡Bienvenidos al mundo de POKÉMON! ¡Me llamo OAK! ¡Pero" "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 355) "la gente me llama el PROFESOR POKÉMON! ¡Este mundo está habitado por" "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 380) "unas criaturas llamadas POKÉMON! Para algunos, los POKÉMON son" "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 405) " mascotas. Pero otros los usan para pelear." "black")
                             (dialogo-oak (+ cont 1) nombre)))

                          ((= cont 2)
                           (begin
                             (sleep 2) ((draw-string ventana) (make-posn 50 350) "En cuanto a mí... Estudio a los POKÉMON como profesión." "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 370) "Asi que tu nombre es:" "black")
                             (sleep 2) ((draw-string ventana) (make-posn 50 390) nombre "black")
                             (dialogo-oak (+ cont 1) nombre)))

                          ((= cont 3)
                           (begin
                             (sleep 2)((draw-string ventana) (make-posn 50 350) "¡Tu propia leyenda POKÉMON está a punto de comenzar!" "black")
                             (sleep 2)((draw-string ventana) (make-posn 50 370) "¡Te espera un mundo de sueños y aventuras con los POKÉMON!" "black")
                             (sleep 2)((draw-string ventana) (make-posn 50 390) "¡Adelante!" "black")
                     
                             (dialogo-oak (+ cont 1) nombre)) (dialogo-oak cont)))
                        ))) (dialogo-oak cont nombre)) )

(dialogo-oak 1 nombre)
