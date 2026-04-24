def boyer_moore_find(text, pattern, start=0, end=None):
    '''
    An analogue of the find method that uses a simplified Boyer-Moore algorithm.
    '''
    if end is None:
        end = len(text)
    
    # Срез текста по заданным границам
    search_text = text[start:end]
    n = len(search_text)
    m = len(pattern)
    
    if m == 0: 
        return start
    if m > n: 
        return -1

    # Таблица "плохого символа"
    bad_char = {char: m - i - 1 for i, char in enumerate(pattern[:-1])}
    bad_char_default = m

    i = 0
    while i <= n - m:
        j = m - 1
        # Сравниваем подстроку с конца
        while j >= 0 and pattern[j] == search_text[i + j]:
            j -= 1
        
        if j < 0:
            return i + start # Нашли совпадение
        else:
            # Сдвиг на основе несовпавшего символа
            char = search_text[i + j]
            shift = bad_char.get(char, bad_char_default)
            # Убеждаемся, что сдвиг всегда положителен относительно текущего j
            i += max(1, shift - (m - 1 - j))
            
    return -1

def find_all_occurrences(text, pattern):
    '''
    Returns a string with the indices of all occurrences, separated by commas.
    '''
    indices = []
    current_pos = 0
    
    while True:
        idx = boyer_moore_find(text, pattern, current_pos)
        if idx == -1:
            break
        indices.append(str(idx))
        current_pos = idx + 1 # Поиск следующего вхождения (с перекрытием)
        
    return ", ".join(indices)


dna_sequence = "JFLKFATCATCATCLKATCGATCGATCG"
sub = "ATC"

first_found = boyer_moore_find(dna_sequence, sub)
all_found = find_all_occurrences(dna_sequence, sub)

print(f"Первое вхождение: {first_found}") # 0
print(f"Все вхождения: {all_found}")      # 0,4,8
