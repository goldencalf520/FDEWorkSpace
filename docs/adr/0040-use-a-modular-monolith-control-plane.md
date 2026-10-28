# Use a modular monolith control plane

The initial control plane will deploy as a modular monolith whose few deep modules own coherent delivery behavior and transactional invariants rather than mirroring the seven user-facing delivery areas as microservices. An Engagement Core module owns the delivery graph, versions, confirmation state, impact propagation, permissions, and history behind one small interface. A module may move behind a network seam only when demonstrated scale, isolation, or deployment variation provides a real second adapter and justifies the operational cost.
