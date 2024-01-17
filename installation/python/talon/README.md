# Talon Python Programming / Setup

WARNING: these are research notes as much as documentation,
take the information you find from here as a guide for further research
more than absolute truth :)

---

NOTE: originally these used the ctre library from robotpy, this appears to have
been migrated to the pheonix6 and pheonix5 libraries respectivaly for 2024, mind the
[robotpy docs](https://robotpy.readthedocs.io/en/stable/) as they are not entierly switched
over for 2024 yet and still include information regaurding the ctre library.
see [robotpy info](https://robotpy.github.io/) for more info on this.

this library can be installed using the pyproject.toml by uncommenting the pheonix5/6 in the
requirements list before syncing and installing. See [installtion page](../README.md) for more info

the following usage example can be found on the official ctr electornics site: the python is at the bottom of the page :)
[simple usage example](https://v6.docs.ctr-electronics.com/en/stable/docs/api-reference/api-usage/api-overview.html#python-imports)

full documentation can be found from the ctre python api docs
[api docs](https://api.ctr-electronics.com/phoenix6/release/python/)
in particular talon information can be found here:
[talon docs](https://api.ctr-electronics.com/phoenix6/release/python/autoapi/phoenix6/hardware/core/core_talon_fx/index.html#phoenix6.hardware.core.core_talon_fx.CoreTalonFX)
