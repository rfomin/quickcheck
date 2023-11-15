
export SOURCE_PORT=/usr/games/chocolate-doom

# Quiet output, convert to lower case, don't restore timestamps,
# overwrite without prompt, extract to extract/ directory.
UNZIPOPTS = -q -LL -o -d extract

OUTPUTS =
WADS = extract/miniwad.wad

all: check

extract/%:
	unzip $(UNZIPOPTS) $< $(subst extract/,,$@)
	@touch $@

extract/miniwad.wad: miniwad.zip
testrunner: $(SOURCE_PORT) extract/miniwad.wad

# Alien Vendetta, Ancalagon 4:13:37
extract/av.wad: pwads/av_new.zip
extract/30av-25337.lmp: demos/avall-41337.zip

output/av.txt: testrunner extract/av.wad extract/30av-25337.lmp
	./testrunner -file av.wad -timedemo extract/30av-25337.lmp >$@

WADS += extract/av.wad
OUTPUTS += output/av.txt

# Cyberdreams, SuperWeaponDude 19:04
extract/cyber110.wad: pwads/cydreams.zip
extract/cyber110.deh: pwads/cydreams.zip
extract/30cyx1904.lmp: demos/cyallx1904.zip

output/cydreams.txt: testrunner extract/cyber110.wad extract/cyber110.deh extract/30cyx1904.lmp
	./testrunner -deh cyber110.deh -file cyber110.wad -timedemo extract/30cyx1904.lmp >$@

WADS += extract/cyber110.wad
OUTPUTS += output/cydreams.txt

# Eternal Doom, ELMLE 2:18:54
extract/eternall.wad: pwads/eternal.zip
extract/30et-13854.lmp: demos/etall-21854.zip

output/eternal.txt: testrunner extract/eternall.wad extract/30et-13854.lmp
	./testrunner -file eternall.wad -timedemo extract/30et-13854.lmp >$@

WADS += extract/eternall.wad
OUTPUTS += output/eternal.txt

# Plutonia 2, Red-XIII 1:05:04
extract/pl2.wad: pwads/pl2.zip
extract/pl2all1.lmp: demos/p2all-6504.zip

output/pl2.txt: testrunner extract/pl2.wad extract/pl2all1.lmp
	./testrunner -gameversion final -file pl2.wad -timedemo extract/pl2all1.lmp >$@

WADS += extract/pl2.wad
OUTPUTS += output/pl2.txt

# Going Down, Daerik 1:52:26
extract/gd.wad: pwads/gd.zip
extract/gdallm15226.lmp: demos/gdallm15226.zip

output/gd.txt: testrunner extract/gd.wad extract/gdallm15226.lmp
	./testrunner -file gd.wad -timedemo extract/gdallm15226.lmp >$@

WADS += extract/gd.wad
OUTPUTS += output/gd.txt

wads: $(WADS)

check: $(OUTPUTS)
	@diff -q --strip-trailing-cr -x .gitignore -r expected output && echo all tests passed

clean:
	rm -rf output/* extract/*

.PHONY: wads check clean all
