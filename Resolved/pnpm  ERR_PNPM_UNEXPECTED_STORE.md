无法通过 `pnpm add -g xxx` 报错误提示 `ERR_PNPM_UNEXPECTED_STORE` 

当前解决方案是，先运行 `pnpm i -g` 再运行 `pnpm add -g xxx` 就可以正常重新安装