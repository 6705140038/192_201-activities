Questions I asked AI
1. What does AttributeError mean?
AI explained that AttributeError happens when Python tries to access something that the object does not have.
In my code, self.fan caused the error because there was no fan attribute. The correct attribute was self.fan_speed.
2. What does RecursionError mean?
AI explained that RecursionError can happen when a function keeps calling itself again and again without stopping.
In my temperature setter, I had:
self.temperature = value
Because temperature is a property, this calls the temperature setter again. The setter calls itself repeatedly, causing recursion.
I changed it to:
self._temperature = value
This stores the value directly in the private attribute and stops the recursion.
3. Why does the constructor need to use the temperature setter?
AI explained that if the constructor directly uses:
self._temperature = temperature
the value does not go through the validation in the setter.
For example, an invalid temperature such as 99 could be accepted.
Using:
self.temperature = temperature
makes the value go through the setter, so the temperature validation is applied when the object is created.
4. Why does is_energy_saving need to use the current temperature?
AI explained that energy-saving status should depend on the current temperature.
If the temperature changes later, a stored value could become outdated.
Therefore, checking the current temperature when is_energy_saving is accessed makes the result reflect the current state of the air conditioner.