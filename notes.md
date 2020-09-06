* ROM type: SL3ROM (SLROM-003; MMC1). 128KB PRG, 128KB CHR
    * No RAM
    
* Mapper reg writes:
    * $BFFF, $DFFF, $FFFF
    
* Most kana/kanji at CHR $F000

* World: switches for character drawing at SL 169
    * write routine 01C066
   
## write routine
   * Takes 2 sucessive frames to draw 1 kana
   * Next char in ZP $0F, $10
       * $OF is is 0x27 if dakuten, 0x00 if none

### kana table (CHR)
    0x01-0x0F:          あいうえおかきくけこさしすせそ
    0x11-0x1F:          たちつてとなにぬねのはひふへほ
    0x21-0x25:          まみむめも
    0x26, 0x28, 0x2A:   やゆよ
    0x27, 0x29:         (dakuten, han-dakuten)
    0x2B-0x2F:          らりるれろ
    0x31-0x33:          わをん
    34-3c               (half width characters)
    3d,3e               (quotes)
    3f                  !
    41...7f             (4 lines similar for katakana. +heart, question mark, period)
    0x80-0x89           0-9
    
    
