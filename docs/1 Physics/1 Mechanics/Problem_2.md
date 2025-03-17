# Problem 2
\documentclass{article}
\usepackage{amsmath}
\usepackage{physics}

\begin{document}

\title{Projectile Motion: Equations and Key Concepts}
\author{Physics Fundamentals}
\date{\today}
\maketitle

\section{Definition of Projectile Motion}
Projectile motion refers to the motion of an object launched into the air under the influence of gravity, following a \textbf{parabolic path}. It consists of two independent motions:
\begin{itemize}
    \item \textbf{Horizontal motion} – Constant velocity (\( v_x \)), as there is no horizontal acceleration (assuming air resistance is negligible).
    \item \textbf{Vertical motion} – Accelerated motion due to gravity (\( g \)).
\end{itemize}

\section{Equations of Motion}

Let:
\begin{itemize}
    \item \( v_0 \) = Initial velocity
    \item \( \theta \) = Launch angle
    \item \( g \) = Acceleration due to gravity (9.81 m/s²)
    \item \( t \) = Time
\end{itemize}

\subsection{1. Horizontal Motion}
\textbf{Velocity:}
\[
v_x = v_0 \cos\theta
\]
(constant, since no horizontal acceleration)

\textbf{Displacement:}
\[
x = v_0 \cos\theta \cdot t
\]

\subsection{2. Vertical Motion}
\textbf{Velocity:}
\[
v_y = v_0 \sin\theta - g t
\]

\textbf{Displacement:}
\[
y = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
\]

\textbf{Time to reach max height:}
\[
t_{\text{max}} = \frac{v_0 \sin\theta}{g}
\]

\textbf{Maximum height:}
\[
h_{\text{max}} = \frac{(v_0 \sin\theta)^2}{2g}
\]

\subsection{3. Time of Flight}
The total time the projectile is in the air:
\[
T = \frac{2 v_0 \sin\theta}{g}
\]

\subsection{4. Range (Horizontal Distance)}
The total horizontal distance traveled:
\[
R = \frac{v_0^2 \sin(2\theta)}{g}
\]

\section{Key Points}
\begin{itemize}
    \item The trajectory follows a \textbf{parabolic path}.
    \item The horizontal and vertical motions are \textbf{independent} of each other.
    \item The optimal launch angle for maximum range is \textbf{45°} (without air resistance).
\end{itemize}

\end{document}
