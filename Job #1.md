whitespaces = [',', '.', ';', ':', ' ', '\t', '\n']

text = "example.txt"


def parse_if_file(text):
    print(text[len(text) - 4 : len(text)])
    if text[len(text) - 4 : len(text)] == ".txt":
        with open(text) as file:
            content = file.read()
        return content
    return text

def parse_text(text, whitespaces):
    text = parse_if_file(text)
    result = []
    current_index = 0
    seq_start_index = 0
    seq_end_index = 0
    for symbol in list(text):
        if symbol in whitespaces:
            seq_end_index = current_index
            result.append(text[seq_start_index : seq_end_index])
            seq_start_index = seq_end_index + 1
        current_index += 1
    if text[len(text) - 1] not in whitespaces:
        result.append(text[seq_start_index:current_index])
    for word in result:
        if word == "":
            result.remove(word)
    return result

print(parse_text(text, whitespaces))
