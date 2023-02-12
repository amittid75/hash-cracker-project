import hashlib

def hash_decrypter(hash, wordlist, algorithm, encoding='ISO-8859-1'):
    with open(wordlist, 'r', encoding=encoding) as f:
        for line in f:
            line = line.strip()
            if hashlib.new(algorithm, line.encode()).hexdigest() == hash:
                return line
    return None

if __name__ == '__main__':
    hash = input('Enter the hash to be decrypted: ')
    algorithm = input('Enter the hash algorithm to use (e.g., md5, sha1, sha256, sha512, etc.): ')
    wordlist = '/usr/share/wordlists/rockyou.txt'
    plain_text = hash_decrypter(hash, wordlist, algorithm)
    if plain_text:
        print(f'The decrypted plain text is: {plain_text}')
    else:
        print('The hash could not be decrypted.')