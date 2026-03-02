# Nginx Docker 安全部署

基于 CIS Docker Benchmark、CIS Nginx Benchmark 标准的 Nginx 安全容器化部署方案。


## 快速开始

```bash
# 1. 克隆本仓库
git clone https://github.com/ihccc-com/cis-docker-nginx.git
cd cis-docker-nginx

# 2. 修改 docker-compose.yml 中的 image 地址
# image: ihccccom/nginx:latest

# 3. 启动容器
docker compose up -d

# 4. 验证
curl http://localhost/
curl -k https://localhost/
```

## 详细教程

📖 完整的 Docker 使用教程请参阅 **[DOCKER-USAGE.md](DOCKER-USAGE.md)**，包括：

- 卷挂载说明
- Nginx 配置文件结构
- ModSecurity WAF 使用
- OWASP CRS 规则集配置
- PHP 集成
- 添加网站
- SSL 证书配置
- 安全配置（Seccomp / AppArmor）
- 日常运维（备份/恢复/更新）
- 常见问题

## 安全特性

| 安全层面 | 实现方式 | 效果 |
|---------|---------|------|
| 内核级防护 | Seccomp + AppArmor | 系统调用白名单 + 强制访问控制 |
| 容器级防护 | 非 root + Capabilities 限制 | 最小权限原则 |
| 应用级防护 | ModSecurity WAF + 安全头 + TLS 1.2/1.3 | Web 应用防火墙 + 传输加密 |
| 运维级防护 | 审计日志 + 健康检查 | 安全运维 |

## 文件结构

```
├── README.md                          # 本文件
├── DOCKER-USAGE.md                    # Docker 使用教程
├── docker-compose.yml                 # Docker Compose 部署文件
└── security/
    ├── seccomp/
    │   └── nginx-seccomp.json        # Seccomp 系统调用白名单
    └── apparmor/
        └── nginx-apparmor-profile    # AppArmor 强制访问控制策略
```

## 许可证

[MIT License](https://github.com/mzwrt/copilot/blob/main/LICENSE)
