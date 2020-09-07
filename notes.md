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
    
### kanji table

    *slotted in around kana. 2 tiles tall each
    
    * Search tools: https://kanji.sljfaq.org/mr.html / https://jisho.org/
    
    0x20, 0x30          物
    0x40, 0x50          金
    0x60, 0x70          病        grade 3     ill,sick
    0xA0, 0xB0          木
    a1,b1               今
    a5,b5               宝        grade 6     treasure,wealth,valuables
    a6,b6               石                    stone (not "right"; left + right are together)
    C6,D6               入
    C9,D9               下
    CA,DA               左
    CB,DB               右
    0xA2, 0xB2          何
    A3,B3               時
    a4,b4               行
    a7,b7               店
    ac,bc               電
    c7,d7               家
    ea,fa               夢
    c0,d0               車
    c1,d1               気
    c2,d2               力
    cc,dc               見
    8d,98               高
    8f,9f               点        *
    cd,dd               口
    
