# Problem 1

\documentclass{article}
\usepackage{amsmath}

\begin{document}

\section{Components of Initial Velocity}
When a projectile is launched with an initial velocity \( v_0 \) at an angle \( \theta \), it has two components:

\begin{itemize}
  \item \textbf{Horizontal velocity:}
    \[
    v_x = v_0 \cos\theta
    \]
  \item \textbf{Vertical velocity:}
    \[
    v_y = v_0 \sin\theta
    \]
\end{itemize}

At any time \( t \), the velocity components are:
\begin{itemize}
  \item \textbf{Horizontal velocity remains constant:}
    \[
    v_x = v_0 \cos\theta
    \]
  \item \textbf{Vertical velocity changes due to gravity:}
    \[
    v_y = v_0 \sin\theta - g t
    \]
    where \( g = 9.8 \, m/s^2 \) (acceleration due to gravity).
\end{itemize}

\section{Time of Flight}
The total time the projectile remains in the air is:
\[
T = \frac{2 v_0 \sin\theta}{g}
\]

\section{Maximum Height}
The highest vertical position reached by the projectile is:
\[
H = \frac{(v_0 \sin\theta)^2}{2g}
\]

\section{Horizontal Range}
The total horizontal distance traveled by the projectile is:
\[
R = \frac{v_0^2 \sin 2\theta}{g}
\]

\section{Equations of Motion}
\textbf{Horizontal Position:}
\[
x = v_0 \cos\theta \cdot t
\]

\textbf{Vertical Position:}
\[
y = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
\]

\section{Key Points about Projectile Motion}
\begin{itemize}
  \item The horizontal velocity remains constant throughout the motion.
  \item The vertical velocity decreases while rising (due to gravity), becomes zero at the peak, and then increases downward.
  \item The trajectory follows a parabolic path.
  \item The time to reach maximum height is \( T/2 \), and then it takes the same time to fall back.
\end{itemize}

\end{document}
