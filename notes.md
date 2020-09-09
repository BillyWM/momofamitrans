## found text

### encoding
* FF for control characters?
    * FF01 seems to be \n
    * FF02 beginning of screen?
    * FF00 end of screen?
    
### confirmed locations

#### intro

* First screen: 0x01EE4 - 0x01F1F
* Third ends 0x01FC0
    * (01FC1 onward isn't read when displaying)
    
#### first screen after title

* 02BDC - starts with FF02 FEFF
    * FExx probably control character for protraits
        * FE60 momo
        * FE65 dog
#### first convo with parents
* 01714F
    
### other locations (probable)
* 0x17EDA seems like probable end for long script block.
    * Followed by FF06 FF02 FF00 then all FF
* 1EACC to 1ED8A
* 13246 to 13553
* 13689 to 13EF9
    * ends on same 6, 2, 0 control pattern
* 140B6 to 14765
* 1485E to 14917
* 14B0B to 14C4B
* 14D34 to 150C2
* 15189 to 154F3
* 155E6 to 158D8
* 15B9B to 1677F
* 16824 to 16C94
* 16EC5 to 17934
* 17A5B to 17EDA
* 0B211 to 0B4B2
    * starts with FF02 FF04 control; what is FF04? Also 2, 0 series preceding it
* 7962 to 07CA2
    * possibly more above. Interrupted by non-text data
* ... to 03D68
* B4B3 to B525 looks like a table of color names
* B543 to BCB2


-------------------

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
    
### kanji table (CHR)

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

    
