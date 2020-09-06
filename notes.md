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
