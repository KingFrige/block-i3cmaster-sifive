# block-i3cmaster-sifive
This is a repository for Improved inter-integrated circuit master.

```bash
module load ruby/ruby/2.5.0
module load synopsys/vcs/O-2018.09-SP2-4
module load riscv_toolchain/sifive-toolchain
module load python/3.7.5
module load wit
module load wit/v0.11.1
module load wake/v0.18.2

wit init workspace_i3c_test -a git@gitlab.internal.starfivetech.com:korben.dong/block-i3cmaster-sifive.git::flow-study
cd workspace_i3c_test

wit add-pkg git@github.com:sifive/environment-bangalore-sifive.git 
wit update
wake --init .

# run simulation
wake -x 'runSimWith (i3cmasterDUT "I3CMasterConfig0") VCS_Waves' | tee log.txt

# view waveforms
dve -vpd build/api-generator-sifive/i3cmasterDUT/sim/vcs/execute/demo/sim.vpd &
```
