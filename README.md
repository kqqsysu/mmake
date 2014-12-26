mmaker为多进程编译,修改自otp/lib/tools/src/make.erl，可以启动多个process进行编译,从而提高编译速度。

本版本优化编译等待，一个文件编译完成后，立即进行后续文件编译,不用等待分组完成。

Usage:
erl -pa ebin -eval "case make:files([\"src/mmake.erl\"], [{outdir, \"ebin\"}]) of error -> halt(1); _ -> ok end" -eval "case mmake:all(8,[$(MAKE_OPTS)]) of up_to_date -> halt(0); error -> halt(1) end."

EMakefile:

{"deps/*", [{i, "include}, {outdir, "ebin"}]}.  

{["src/*"], [{i, "include}, {outdir, "ebin"}]}.  

参考 https://github.com/litaocheng/mmake
