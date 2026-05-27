# hi, I'm Richard 👋

Backend engineer / architect from southern Brazil. Twenty-five years of mostly Python, mostly Postgres, mostly async. Sometimes wiring network cables, often coding things that matter.

```python
import typing as t
from dataclasses import dataclass, field, InitVar


@dataclass
class Being:
    """An entity with code, hobbies, and opinions.

    >>> me = Being(
    ...     name="Richard Kuesters",
    ...     based_in="southern Brazil",
    ...     since=2000,
    ...     stack=("Python", "PostgreSQL", "async"),
    ...     underrated=("frogs", "insects", "documentation"),
    ...     initial_loves=("wifey", "son", "dog", "beach"),
    ... )
    >>> me.based_in
    'southern Brazil'
    >>> "frogs" in me.underrated
    True
    >>> "beach" in me.loves
    True
    >>> me.love("FOSS")
    >>> "FOSS" in me.loves
    True
    """

    name: str
    based_in: str
    since: int
    stack: tuple[str, ...]
    underrated: t.Iterable[str] = ()
    initial_loves: InitVar[t.Iterable[str]] = ()
    currently: tuple[str, ...] = ()
    tooling: dict[str, str] = field(default_factory=dict)
    coffee: bool = True
    _loves: frozenset[str] = field(init=False, default_factory=frozenset)

    def __post_init__(self, initial_loves: t.Iterable[str]) -> None:
        self.underrated = frozenset(self.underrated)
        self._loves = frozenset(initial_loves)

    @property
    def loves(self) -> frozenset[str]:
        return self._loves

    def love(self, *items: str) -> None:
        """Add to loves. You can add. You can't remove."""
        self._loves = self._loves | frozenset(items)


if __name__ == "__main__":
    richard = Being(
        name="Richard Kuesters",
        based_in="southern Brazil",
        since=2000,
        stack=("Python", "PostgreSQL", "async"),
        underrated=("frogs", "insects", "documentation", "the Theory of Constraints"),
        initial_loves=("wifey", "son", "dog", "beach"),
        currently=("running the multi-quarter roadmap", "Claude Code as a platform"),
        tooling={"ai": "Claude Code", "shell": "zsh"},
    )
    assert richard.name == "Richard Kuesters"
    assert 2026 - richard.since == 26
    assert "frogs" in richard.underrated
    assert "beach" in richard.loves
    assert richard.coffee
    richard.love("FOSS", "long-running OSS friendships")
    assert "FOSS" in richard.loves
```

I helped run [Sanic](https://sanic.dev) for a while (former core dev) and got a public "shout out to @vltr for all his work" from the `sanic-jwt` lead maintainer. That one's archived in the docs, which is nice. I also authored a handful of PyPI packages that did their job before the ecosystem caught up.

These days I'm the sole backend voice at a US workforce-management SaaS, running the multi-quarter roadmap that keeps the lights on. I treat Claude Code as a platform to engineer around (hooks, skills, MCP servers, agents), not just to prompt.

Off-keyboard: CNC, 3D printing, wood-carving, GNOME Shell tinkering, Arch Linux as a hobby, craft brewing, F1, and a strong opinion that insects and frogs deserve more love.

## Where to find me

[LinkedIn](https://www.linkedin.com/in/rkuesters/) · email in profile.

---

```text
         .--.
        /    \
       | o  o |
        \ ww /
         '--'
        ribbit
```
