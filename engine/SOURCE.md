# Engine source

These files are copied unchanged from the Clover framework repository
(`Santhoshsathish94/clover-framework`, `clover-ai-system/studio/clover/`). They come from commit `c00a4f93` on
branch `fix/studio-ui-504`, which is not merged yet. The git blob ids must match that commit:

```
e758042075223a209fcec320656d015b0f442be9  collective_repo.py
67fa402c085e6166c454328aa9f5af1a2e1d99ea  collective_gateway.py
be8cf69d3d87151aca610c4fd26f2d6b56308137  collective.py
0d8e85db63a50b766d3714cc456e4417b233a38a  collective_evaluator.py
e5ccaf842104fb7d833ec69a2a0fa50c354247b1  core_registry.py
924571e6e4ce7fba33b6f3359f8f4775898f768c  personal.py
23e7eb218ed1cb60ede6d9bc865e6139bd3b0dfb  semantics.py
f9802fcafb2b4139bb20404c10a63c929e19635e  clover_cycle.py
```

To check them, run `git ls-tree HEAD engine/` here, and `git ls-tree c00a4f93 clover-ai-system/studio/clover/` in the
framework.

The files use only the Python standard library. To update them, copy the new versions from the framework, then
update this list and the commit.
