 # A ⇄ B gamepad swap
 - За замовчуванням, гра використовує Японську розкладку клавіш для геймпаду (A -- відміна, B -- підтвердження). Ви можете скористатися цим модом, аби замінити розкладку на Західну.
 - Для цього необхідно вставити скрипт нижче, у файл main.js одразу після "use strict". Або ви можете завантажити вже модифікований файл main.js у цій же теці

 ```js
"use strict";

  const desc = Object.getOwnPropertyDescriptor(Gamepad.prototype, "buttons");
  Object.defineProperty(Gamepad.prototype, "buttons", {
    get() {
      const btn = desc.get.call(this);

      if (!btn || btn.length < 2) return btn;

      // Створюємо копію списку кнопок
      const swapped = btn.slice();

      // Міняємо місцями A (0) та B (1)
      swapped[0] = btn[1];
      swapped[1] = btn[0];

      return swapped;
    }
  });

// ... Решта коду
 ```
