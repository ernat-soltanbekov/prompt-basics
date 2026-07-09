# Упражнение 3: Few-Shot, контроль формата вывода

### Запрос без примеров (Zero-shot)
**Мой промпт:** Напиши документацию для функции на Go: `func IsNegative(nb int) bool`

**Ответ GPT:**
В Go документация обычно начинается с имени экспортируемой функции и кратко описывает, что она делает.
// IsNegative reports whether nb is a negative number.
// It returns true if nb is less than zero; otherwise, it returns false.
func IsNegative(nb int) bool {
	return nb < 0
}
[Далее ИИ привел русскоязычный вариант комментариев и добавил лекцию про стандарты go doc и стиль сообщества].

---

### Запрос с примерами (Few-shot)
**Мой промпт:** Напиши документацию для функции на Go, используя строго следующий формат:
Функция: `func Add(a int, b int) int`
Док: // Add takes two integers and returns their sum.

Функция: `func ToUpper(s string) string`
Док: // ToUpper takes a string and returns it converted to uppercase letters.

Функция: `func IsNegative(nb int) bool`
Док:

**Ответ GPT:**
// IsNegative takes an integer and returns true if it is negative, otherwise false.

---

### Анализ (Reflection)
Предоставление примеров (few-shot) кардинально изменило консистентность и формат ответа. При zero-shot запросе модель выдала избыточный текст: лекцию о стандартах Go, реализацию самой функции и варианты на разных языках. Как только я добавил паттерн "вход -> выход", модель мгновенно подстроилась под контекст, полностью исключила "разговорный" мусор и выдала строго одну строку на английском языке, идеально вписывающуюся в заданный формат.