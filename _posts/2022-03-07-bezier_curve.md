# Quadratic Bézier curve

[2022-03-07]

![](/img/2022-03-07.png)

We can draw of a quadratic Bézier curve by connecting two points **P0** and **P2** where a third point, **P1** attracts the connecting line towards it.

```
using Plots
function BezCurve(P0, P1, P2, vec_t)
    vec_x = []
    vec_y = []
    for t in vec_t
        P = (1-t)*((1-t)*P0 + (t*P1)) + t*((1-t)*P1 + (t*P2))
        append!(vec_x, P[1])
        append!(vec_y, P[2])
    end
    return (vec_x, vec_y)
end

P0 = [-1,0]
P1 = [1,0]
P2 = [0,1]
vec_t = range(0,1;length=100)
x, y = BezCurve(P0, P1, P2, vec_t)
plt = plot([-1.1, 1.1], [0, 1], linecolor=:white, legend=false)
plot!(plt, x, y, linewidth=5)
mat = reshape(vcat(P0,P1,P2), (2,3))'
scatter!(plt, mat[:,1], mat[:,2], series_annotations=text.(["P0", "P1", "P2"], :bottom))
savefig(plt, "2022-03-07.png")
```