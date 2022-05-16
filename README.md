First time eBPF
---------------

1. Verifier que le kernel supporte les BPF kprobes + uprobes

```
grep -i BPF /usr/src/linux-headers-5.4.0-109-generic/.config
CONFIG_CGROUP_BPF=y
CONFIG_BPF=y
CONFIG_BPF_SYSCALL=y
CONFIG_BPF_JIT_ALWAYS_ON=y
CONFIG_BPF_UNPRIV_DEFAULT_OFF=y
CONFIG_IPV6_SEG6_BPF=y
CONFIG_NETFILTER_XT_MATCH_BPF=m
CONFIG_BPFILTER=y
CONFIG_BPFILTER_UMH=m
CONFIG_NET_CLS_BPF=m
CONFIG_NET_ACT_BPF=m
CONFIG_BPF_JIT=y
CONFIG_BPF_STREAM_PARSER=y
CONFIG_LWTUNNEL_BPF=y
CONFIG_HAVE_EBPF_JIT=y
CONFIG_BPF_EVENTS=y
CONFIG_BPF_KPROBE_OVERRIDE=y
CONFIG_TEST_BPF=m
```

Les options necessaires sont CONFIG_BPF, CONFIG_BPF_SYSCALL, CONFIG_BPF_JIT_ALWAYS_ON, CONFIG_HAVE_EBPF_JIT, CONFIG_BPF_EVENTS et CONFIG_BPF_KPROBE_OVERRIDE.

2. Utiliation du facilitateur eBPF high-level tracing du projet [iovisor](https://github.com/iovisor/bpftrace)

```
sudo apt-get install -y bpftrace
```

Compiler le programme de test :
```
gcc -Wall -o hello_world hello_world.c
chmod +x hello_world && ./hello_world
Hello World : 487
sudo ./first_bpftrace_uprobe
Attaching 2 probes...
```
