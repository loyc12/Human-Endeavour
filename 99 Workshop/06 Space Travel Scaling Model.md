# Space Travel Scaling Model

**Status: Approved numerical baseline; mechanism details open**

## Purpose

This author-facing worksheet provides a common set of formulae for testing how travel capability produces—**or does not produce**—exploration, infrastructure, and settlement. It is deliberately independent of a selected FTL mechanism. Its purpose is to prevent a maximum cruise speed from silently becoming the scale of the civilisation.

The default interpolation model is: **logistic growth** for a technology's general capability, **exponential maturation** for each newly commissioned route, and the **minimum of several bottlenecks** for exploration and settlement. It therefore represents a slow, expensive experimental period; a faster infrastructure-led takeoff; and a mature ceiling without assuming that population movement or colonisation accelerates at the same rate.

Use it with [[99 Workshop/02 Spacetime Engineering|Spacetime Engineering]] and [[99 Workshop/05 Milky Way Astropolitical Foundations|Milky Way Astropolitical Foundations]]. The equations describe planning models, not exact physical law or in-universe public knowledge.

## Units and Variables

Use light-years, years, and multiples of light speed. In these units, `1c = 1 ly/year`.

| Symbol | Meaning |
| --- | --- |
| `D` | Route distance in light-years. |
| `d` | Local-system distance in metres, kilometres, or AU. |
| `v_free` | Safe, self-navigated FTL cruise speed without mature route support. |
| `v_lane` | Cruise speed on a maintained, surveyed, infrastructure-supported route. |
| `v_max` | Exceptional, top-speed service on the best route and with the best vessel. It is not a normal planning speed. |
| `I` | Infrastructure quality from `0` (none) to `1` (mature route). |
| `L` | Maximum safe leg length before a staging, navigation, or support stop is required. |
| `t_entry`, `t_exit` | Time for preparation, calibration, and arrival handling per leg. |
| `t_wait` | Scheduling, inspection, berth, cargo, or passenger delay. |
| `t_cool` | Cooldown, maintenance, heat rejection, or recharge delay. |
| `t_scan` | Survey and validation time at a prospective destination. |
| `t_build` | Time to establish a viable settlement or route-support site. |
| `v_exp` | Exploration-front advance rate along a selected corridor. |
| `v_set` | Durable-settlement-front advance rate. This is a demographic and institutional rate, not vessel speed. |
| `t` | Years since official FTL discovery. |
| `t_50` | Nominal midpoint of a technological capability's takeoff after FTL discovery. |
| `w_10-90` | Years taken for a capability to rise from ten to ninety percent of its practical mature increase. |
| `a_route` | Age of a particular route since it was commissioned. |
| `\tau_route` | Characteristic time for a route to acquire mature infrastructure and operating practice. |
| `H` | Service class: `0` for ordinary service and `1` for an exceptional express service. |

## 1. Individual Interstellar Travel

### Default time interpolation

Do not interpolate speeds linearly by default. Technical development and adoption usually have a long slow beginning, a period of compounding improvement, and a practical ceiling. For any technology-dependent speed band `x`, use a logistic curve:

$$
L(t;t_{50},w_{10-90}) = \frac{1}{1+e^{-k(t-t_{50})}}, \qquad k = \frac{2\ln 9}{w_{10-90}}
$$

$$
\widetilde L(t;t_{50},w_{10-90}) = \frac{L(t;t_{50},w_{10-90})-L(0;t_{50},w_{10-90})}{1-L(0;t_{50},w_{10-90})}, \qquad
v_x(t) = v_{x,\mathrm{start}} + \left(v_{x,\infty}-v_{x,\mathrm{start}}\right)\widetilde L(t;t_{50,x},w_{10-90,x})
$$

`v_x,start` is the usable capability at official FTL discovery (`t = 0`), and `v_x,∞` is the practical mature ceiling, not an inviolable physical limit. The normalisation makes the selected starting value exact. The `10--90` parameter is more intuitive than a raw steepness constant: a smaller value means a sharper technological revolution. When the nominal midpoint is well after discovery, it remains a close practical description of the midpoint of adoption.

Apply the curve separately to three raw capabilities:

$$
v_{\mathrm{free}}(t), \qquad v^*_{\mathrm{lane}}(t), \qquad v^*_{\mathrm{max}}(t)
$$

The free-flight curve should take off earliest and level off at the lowest speed. Mature-corridor capability follows later and rises higher. The exceptional maximum should be latest, steepest, and highest; it represents specialist vessels on exceptionally good routes, not a speed every ship can use. Apply the physical ordering explicitly:

$$
v^*_{\mathrm{lane}}(t) = \max\left(v_{\mathrm{free}}(t),v_{\mathrm{lane,raw}}(t)\right), \qquad
v^*_{\mathrm{max}}(t) = \max\left(v^*_{\mathrm{lane}}(t),v_{\mathrm{max,raw}}(t)\right)
$$

This means that early in the express curve's development, the best available service is simply the ordinary mature-corridor service; the special express premium emerges only later.

This is the recommended historical shape for the setting: early FTL can cross `1c` without making broad reconnection cheap or rapid; routine high-speed travel arrives only after technology, route construction, and operating institutions have all matured.

### Route maturation and service class

High speeds should also depend on the age and quality of a *specific* route. Model its infrastructure quality as:

$$
I(a_{\mathrm{route}}) = 1-e^{-a_{\mathrm{route}}/\tau_{\mathrm{route}}}
$$

Use the resulting quality to calculate ordinary service:

$$
v_{\mathrm{ordinary}}(t,a_{\mathrm{route}}) =
v_{\mathrm{free}}(t)^{1-I}
\left(v^*_{\mathrm{lane}}(t)\right)^I
$$

Then calculate a service's actual cruise speed as:

$$
v_{\mathrm{service}}(t,a_{\mathrm{route}},H) =
v_{\mathrm{ordinary}}
\left(
\frac{v^*_{\mathrm{max}}(t)}{v_{\mathrm{ordinary}}}
\right)^{H I^\gamma}
$$

`\gamma` controls how strongly exceptional service depends on route quality. A value near `1` is a moderate requirement; a value near `2` makes near-perfect infrastructure necessary for the highest speeds. Thus a ship with advanced hardware falls back toward `v_free` on an unprepared route, while a mature corridor may support a routine `v_lane` service and, rarely, a 500c express service.

The former static interpolation is a special case of this model: use the current `I` for a route and set `H = 0` for ordinary service.

For a single, direct FTL trip with no intermediate support:

$$
T_{\mathrm{trip}} = \frac{D}{v_{\mathrm{eff}}} + t_{\mathrm{entry}} + t_{\mathrm{exit}} + t_{\mathrm{wait}} + t_{\mathrm{cool}}
$$

For this trip, set `v_eff = v_service(t,a_route,H)`. The geometric form intentionally prevents a half-complete route from receiving half of an extreme speed bonus. Replace it with stepwise classes if the eventual mechanism has discrete navigation or endpoint requirements.

For a route divided into `n` legs, where `n = \lceil D/L \rceil`:

$$
T_{\mathrm{route}} = \sum_{j=1}^{n}\left(\frac{D_j}{v_{\mathrm{eff},j}} + t_{\mathrm{entry},j} + t_{\mathrm{exit},j} + t_{\mathrm{cool},j}\right) + t_{\mathrm{wait}}
$$

The overhead terms are how infrastructure retains importance even when headline FTL speeds are high. A 500c express service can still be unavailable, scheduled, expensive, or impossible away from mature endpoints.

### Selected modern travel classes

These are the selected balanced-model travel bands. Exact fare structure, endpoint hardware, mass limits, and communications consequences remain open.

| Route condition | Candidate cruise band | Intended effect |
| --- | ---: | --- |
| Unprepared or independently navigated route | 10--30c | Exploration is fast but not effortless; calibration, risk, and long-distance provisioning remain significant. |
| Developing route or heavy freight | 25--75c | Regional movement is useful, but schedule and infrastructure visibly matter. |
| Mature ordinary corridor | 75--150c | Nearby systems are weeks apart and regional trips are months apart. |
| Exceptional express corridor | Up to 500c | A premium, infrastructure-dependent maximum rather than the universal speed of civilisation. |

At 500c, a ten-light-year corridor takes about seven days of cruise time and a hundred-light-year corridor about seventy-three days, before overhead. At 100c, those figures are about thirty-seven days and one year.

### Selected balanced-model parameters

The time origin is FTL discovery at 260 BCD. The values below use the logistic interpolation defined above; `t_50` and `w_10-90` are years after discovery.

| Capability or constraint | Discovery-date value | Mature ceiling | `t_50` | `w_10-90` or `\tau` |
| --- | ---: | ---: | ---: | ---: |
| `v_free` | 1c | 30c | 135 years | 110 years |
| `v_lane` | 1c | 150c | 150 years | 95 years |
| `v_max` | 1c | 500c | 215 years | 50 years |
| `v_infra` | 0.1c | 8c | 160 years | 110 years |
| `I(a_route)` | 0 | 1 | — | `\tau_route = 25` years |
| Exceptional-service dependence | — | — | — | `\gamma = 2` |
| Exploration efficiency | — | — | — | `\epsilon_exp = 0.65` |
| Settlement-choice ceiling | 0.12c | 9c | 170 years | 110 years |

The settlement-choice ceiling represents `\ell_choice/(t_decision + t_build + t_support)` and is still limited by exploration and infrastructure. It therefore does not imply that a ship's cruise capability becomes a settlement-front capability.

With an 8,000-year history, 260 years of FTL, and a 0.05c pre-FTL average frontier rate, this parameter set produces these characteristic scales:

| Quantity | Selected result | Interpretation |
| --- | ---: | --- |
| Pre-FTL diaspora reach | ~390 ly | Old, uneven human-descended and post-human space. |
| Active maintained-route extent | ~820 ly | Irregular core-centred networks with reliable support, not a circle of equal access. |
| Durable settlement extent | ~790 ly | Characteristic serviceable settlement frontier; rare outliers do not redefine normal civilisation. |
| Selected exploration corridors | ~1,230 ly | Surveyed spokes and contact zones, not a filled or uniformly known volume. |

Around 100 BCD, mature corridors already support roughly 90c ordinary service; 500c express service is a much more recent, infrastructure-dependent achievement.

## 2. Local-System Travel

Use normal propulsion, acceleration, and port handling to keep travel inside a system materially distinct from FTL travel. For a vessel that accelerates at `a`, then brakes at the same rate, with a speed cap `v_cap`:

$$
T_{\mathrm{local}} =
\begin{cases}
2\sqrt{d/a}, & d \leq v_{\mathrm{cap}}^2/a \\
d/v_{\mathrm{cap}} + v_{\mathrm{cap}}/a, & d > v_{\mathrm{cap}}^2/a
\end{cases}
+ t_{\mathrm{traffic}} + t_{\mathrm{dock}}
$$

The first case is a continuous accelerate-and-brake journey; the second includes a cruising phase. Local infrastructure can lower `t_traffic` and `t_dock`, permit higher safe `v_cap`, provide refuelling or tugs, and make certain orbits practically central. It does not need to make every point in a system equally convenient.

## 3. Infrastructure Growth

Fast corridor travel must be preceded by the ability to survey, build, certify, and maintain the corridor. A simple route-build time is:

$$
T_{\mathrm{lane}}(D) = T_{\mathrm{survey}}(D) + \frac{D}{v_{\mathrm{builder}}} + t_{\mathrm{install}}(D) + t_{\mathrm{certify}}
$$

Where installation can be approximated as either a fixed project duration or `t_install(D) = D/b`, with `b` as the rate at which a construction programme can extend and support a lane.

Infrastructure construction also improves over history, but normally later and more slowly than bare drive capability. Use another logistic curve for the rate at which a civilisation can extend *maintained* route support:

$$
v_{\mathrm{infra}}(t) = v_{\mathrm{infra},\mathrm{start}} +
\left(v_{\mathrm{infra},\infty}-v_{\mathrm{infra},\mathrm{start}}\right)
\widetilde L(t;t_{50,\mathrm{infra}},w_{10-90,\mathrm{infra}})
$$

The active infrastructure radius is then:

$$
R_{\mathrm{lane}}(t) = R_0 + \int_0^t v_{\mathrm{infra}}(u)\,du
$$

Use this as a social and industrial limit, not merely a construction schedule. Beyond `R_lane`, ships may still travel, but they lack the reliable navigation, maintenance, rescue, scheduling, and throughput that make high speeds routine. Sparse branches and exceptional projects need not make this radius circular or continuous.

## 4. Exploration

For one target system:

$$
T_{\mathrm{target}} = T_{\mathrm{outbound}} + t_{\mathrm{scan}} + t_{\mathrm{validation}} + T_{\mathrm{return\ or\ relay}}
$$

For a fleet of `F` equivalent survey assets, the rough target throughput is:

$$
\Lambda_{\mathrm{survey}} \approx \frac{F\,u}{T_{\mathrm{target}}}
$$

where `u` is the utilisation fraction after repairs, safety margins, competing duties, and losses. This is usually more useful than assuming every reachable star has been examined.

Exploration speed is not the current bare cruise speed. It is the rate at which a programme can select, reach, investigate, validate, and record progressively more distant targets. Model its technological ceiling as a fraction of free-flight capability:

$$
v_{\mathrm{exp,tech}}(t) = \epsilon_{\mathrm{exp}}\,v_{\mathrm{free}}(t), \qquad 0 < \epsilon_{\mathrm{exp}} < 1
$$

Then cap it by fleet throughput and navigation work:

$$
v_{\mathrm{exp}}(t) \lesssim \min\left(
v_{\mathrm{exp,tech}}(t),
\frac{\ell_{\mathrm{survey}}}{T_{\mathrm{target}}/F_{\mathrm{effective}}}
\right)
$$

`\ell_survey` is the typical outward step between validated targets. `F_effective` is the number of genuinely available survey assets, after accounting for geography and competing work; it need not equal the total fleet.

Along a deliberately maintained exploration corridor:

$$
R_{\mathrm{explored}}(t) = R_0 + \int_0^t v_{\mathrm{exp}}(u)\,du
$$

This produces a *spoke*, route, or selected set of targets—not a filled sphere. To estimate the number of candidate systems actually surveyed, multiply the broad geometric volume by a coverage fraction `f_cov`:

$$
N_{\mathrm{surveyed}} \approx f_{\mathrm{cov}}\,n_\star\,V(R)
$$

For a small, approximately spherical local volume, `V(R) = 4\pi R^3/3`. For a much wider, thin-disc region, use `V(R) \approx \pi R^2h`, where `h` is the effective settled-disc thickness. The decisive setting choice is often `f_cov`, not `R`.

## 5. Settlement

The basic historical model is:

$$
R_{\mathrm{settlement}}(t) = R_0 + \int_0^t v_{\mathrm{set}}(u)\,du
$$

Here `v_set` means the advance of the **serviceable, recurring settlement frontier**. It should be selected independently of cruise speed. A useful constraint model is:

$$
v_{\mathrm{set}}(t) \lesssim \min\left(
v_{\mathrm{exp}}(t),\;
v_{\mathrm{infra}}(t),\;
\frac{\ell_{\mathrm{choice}}(t)}{t_{\mathrm{decision}}(t) + t_{\mathrm{build}}(t) + t_{\mathrm{support}}(t)}
\right)
$$

`\ell_choice` is the outward step normally accepted by founders or sponsoring institutions. The final term makes lack of interested colonists, political willingness, industrial capacity, and the time needed to establish reliable support visible parts of expansion.

The number of viable new settlements per year is bounded by several distinct bottlenecks:

$$
\Lambda_{\mathrm{settle}} \leq \min\left(
\Lambda_{\mathrm{survey}}p_{\mathrm{select}}p_{\mathrm{success}},
\frac{B}{C_{\mathrm{project}}},
\frac{M}{m_{\mathrm{founders}}},
\frac{K}{k_{\mathrm{support}}}
\right)
$$

Where `B` is available capital or public capacity, `C_project` is project cost, `M` is willing migrants per year, `m_founders` is the viable founding population, and `K/k_support` represents limited route, maintenance, administrative, medical, or industrial support. In this model, lack of interested colonists is represented directly by `M`, rather than being asked to do the impossible work of slowing ships.

### Core-launched versus frontier-launched settlement

When most seed ships launch from a compact historical core, do **not** automatically add the pre-FTL radius to every FTL-era project. Track the origin of each project:

$$
D_j = \left|\mathbf{x}_{\mathrm{target},j} - \mathbf{x}_{\mathrm{origin},j}\right|
$$

For the main civilisation, use a median or 90th-percentile radius of active settlements rather than the most distant outlier:

$$
R_{50},R_{90} = Q_{50},Q_{90}\left(\left|\mathbf{x}_{\mathrm{settlement}}-\mathbf{x}_{\mathrm{Earth}}\right|\right)
$$

An isolated prestige mission can be very far away without redefining the scale of normal life. This is especially important if only a few frontier worlds launch independent expeditions.

## 6. Calculation Method and Timeline Worksheet

For a selected historical span, evaluate the time-varying functions in small equal steps—one year is normally adequate for this setting—and use midpoint integration:

$$
R(t+\Delta t) \approx R(t) + v\left(t+\frac{\Delta t}{2}\right)\Delta t
$$

Use this for `R_lane`, `R_explored`, and `R_settlement`. It handles the minimum functions above without pretending that their integral has a simple closed form. If a specific historical event changes investment, law, war, migration appetite, or the FTL mechanism, alter the affected parameters from that date onward rather than forcing a smooth curve through the disruption.

For each historical period, record the logistic and social parameters rather than one headline FTL speed:

| Capability or constraint | Discovery-date value | Mature ceiling | `t_50` | `w_10-90` or `\tau` | Notes |
| --- | ---: | ---: | ---: | ---: | --- |
| `v_free` |  |  |  |  | Bare drive and navigation capability |
| `v_lane` |  |  |  |  | Ordinary mature-corridor service |
| `v_max` |  |  |  |  | Exceptional express service |
| `v_infra` |  |  |  |  | Route-construction and support-front rate |
| `I(a_route)` | 0 | 1 |  | `\tau_route` | Maturation of each commissioned route |
| `\ell_choice/(t_decision+t_build+t_support)` |  |  |  |  | Settlement appetite and support bottleneck |

The selected balanced model uses a long 0.05c sublight era; FTL discovery with a low `v_free` floor; a deliberately delayed `v_lane` takeoff; a still later, steeper `v_max` curve toward 500c; and a settlement bottleneck that remains far below cruise capability. Its values are recorded above and in [[02 World/01 History/00 Broad Historical Timeline|Broad Historical Timeline]].

## Interpretation Rules

- A maximum speed is an engineering capability. It does not establish a normal route, a migration flow, or a political frontier.
- Technology can improve smoothly while history does not. Use logistic capability curves by default, route-age maturation for individual connections, and explicit parameter changes for wars, discoveries, regulation, or demographic shifts.
- A route can be fast for people but slow for bulk mass, dangerous goods, large habitats, or emergency repair.
- Exploration can outrun settlement; settlement can outrun political integration; communication can differ from both.
- Route infrastructure creates hubs, dependencies, chokepoints, maintenance occupations, unequal access, and reasons the true core remains important even when travel is rapid.
- A settlement map should show dense clusters, maintained corridors, sparse projects, and imperfectly surveyed directions—not only distance rings.
- Select exact values only after choosing the FTL technology's range, navigation, energy, cooldown, and failure logic. Then test the result against the crew's expectations and the multi-century Andromeda return problem.
