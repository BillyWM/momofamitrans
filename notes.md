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
    
      (in column on left)
    0x20, 0x30    物
    0x40          金
    0x60          病        grade 3     ill,sick
    
      (rows)
      (first is not full row)
      
    0x8B, 0x9B          
    0x8C
    0x8D          高
    0x8E
    0x8F          点        *      
      
      (full rows)
    0xA0, 0xB0    木
    0xA1          今
    0xA2          何
    0xA3          時
    0xA4          行
    0xA5          宝        grade 6     treasure,wealth,valuables
    0xA6          石                    stone (not "right"; left + right are together @0xCA, 0xCB)
    0xA7          店
    0xA8          員        *
    0xA9          工                    ? unsure of this one; much wider on bottom in CHR
    0xAA          
    0xAB              
    0xAC          電
    0xAD          器        grade 4     vessel, container, utensil/tool/instrument, ability
    0xAE          洋        grade 3     ocean, sea, foreign, western style
    0xAF          

    0xC0          車
    0xC1          気
    0xC2          力
    0xC3
    0xC4
    0xC5
    0xC6          入
    0xC7          家
    0xC8
    0xC9          下
    0xCA          左
    0xCB          右
    0xCC          見
    0xCD          口
    0xCE
    0xCF

    0xE0
    0xE1
    0xE2
    0xE3
    0xE4
    0xE5          土              (unsure; cross-stroke seems high in CHR)
    0xE6          出
    0xE7
    0xE8          外
    0xE9          大
    0xEA          夢
    0xEB          思     grade 2     think
    0xEC
    0xED
    0xEE
    0xEF

    
