# Model Claim: Contact Pressure

Use when claims depend on pressure distribution, contact area, peak contact
pressure, penetration, sliding, frictional stress, sealing, or interface loading.

Check:

- Contact pressure is highly sensitive to mesh, contact formulation, and
  friction/penalty settings.
- Report contact pair definition, contact algorithm, friction law, and local
  mesh refinement.
- Use integrated or region-averaged quantities when peak values are unstable.
- Do not infer wear, damage, or biological response from pressure alone unless a
  linked model or validation is supplied.

Wording: "pressure was redistributed over a larger contact region" is safer
than "wear was reduced" without a wear model or experiment.
