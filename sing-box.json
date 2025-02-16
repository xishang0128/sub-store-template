{
  "dns": {
    "fakeip": {
      "enabled": true,
      "inet4_range": "198.18.0.0/15",
      "inet6_range": "fc00::/18"
    },
    "servers": [
      {
        "tag": "google",
        "address": "https://8.8.8.8/dns-query",
        "detour": "proxy"
      },
      {
        "tag": "ali",
        "address": "https://223.5.5.5/dns-query",
        "detour": "direct"
      },
      {
        "tag": "fakeip",
        "address": "fakeip"
      }
    ],
    "rules": [
      {
        "outbound": "any",
        "action": "route",
        "server": "ali",
        "disable_cache": true
      },
      {
        "clash_mode": "Direct",
        "action": "route",
        "server": "ali"
      },
      {
        "clash_mode": "Global",
        "action": "route",
        "server": "fakeip"
      },
      {
        "query_type": "HTTPS",
        "action": "reject"
      },
      {
        "query_type": [
          "A",
          "AAAA"
        ],
        "action": "route",
        "server": "fakeip",
        "rewrite_ttl": 1
      },
      {
        "rule_set": "cn_domain",
        "action": "route",
        "server": "ali"
      }
    ],
    "final": "google",
    "independent_cache": true
  },
  "route": {
    "rules": [
      {
        "action": "sniff",
        "sniffer": [
          "http",
          "tls",
          "quic",
          "dns"
        ],
        "timeout": "500ms"
      },
      {
        "type": "logical",
        "mode": "or",
        "rules": [
          {
            "port": 53
          },
          {
            "protocol": "dns"
          }
        ],
        "action": "hijack-dns"
      },
      {
        "ip_is_private": true,
        "action": "route",
        "outbound": "direct"
      },
      {
        "clash_mode": "Global",
        "action": "route",
        "outbound": "GLOBAL"
      },
      {
        "clash_mode": "Direct",
        "action": "route",
        "outbound": "direct"
      },
      {
        "rule_set": "bilibili_domain",
        "action": "route",
        "outbound": "bilibili"
      },
      {
        "rule_set": [
          "netflix_ip",
          "netflix_domain"
        ],
        "action": "route",
        "outbound": "netflix"
      },
      {
        "rule_set": "bahamut_domain",
        "action": "route",
        "outbound": "bahamut"
      },
      {
        "rule_set": "youtube_domain",
        "action": "route",
        "outbound": "youtube"
      },
      {
        "rule_set": "openai_domain",
        "action": "route",
        "outbound": "openai"
      },
      {
        "type": "logical",
        "mode": "and",
        "rules": [
          {
            "rule_set": "proxy_domain"
          },
          {
            "invert": true,
            "rule_set": [
              "cn_domain",
              "apple_domain",
              "google_domain",
              "telegram_domain",
              "netflix_domain"
            ]
          }
        ],
        "action": "route",
        "outbound": "proxy"
      },
      {
        "action": "resolve"
      },
      {
        "rule_set": [
          "telegram_ip",
          "telegram_domain"
        ],
        "action": "route",
        "outbound": "telegram"
      },
      {
        "rule_set": [
          "google_ip",
          "google_domain"
        ],
        "action": "route",
        "outbound": "google"
      },
      {
        "rule_set": [
          "apple_ip",
          "apple_domain"
        ],
        "action": "route",
        "outbound": "apple"
      },
      {
        "rule_set": [
          "cn_ip",
          "cn_domain"
        ],
        "action": "route",
        "outbound": "cn"
      }
    ],
    "rule_set": [
      {
        "tag": "apple_ip",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geoip/apple.srs",
        "download_detour": "direct"
      },
      {
        "tag": "apple_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/apple.srs",
        "download_detour": "direct"
      },
      {
        "tag": "bahamut_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/bahamut.srs",
        "download_detour": "direct"
      },
      {
        "tag": "bilibili_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/bilibili.srs",
        "download_detour": "direct"
      },
      {
        "tag": "cn_ip",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo/geoip/cn.srs",
        "download_detour": "direct"
      },
      {
        "tag": "cn_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/cn.srs",
        "download_detour": "direct"
      },
      {
        "tag": "google_ip",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geoip/google.srs",
        "download_detour": "direct"
      },
      {
        "tag": "google_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/google.srs",
        "download_detour": "direct"
      },
      {
        "tag": "netflix_ip",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geoip/netflix.srs",
        "download_detour": "direct"
      },
      {
        "tag": "netflix_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/netflix.srs",
        "download_detour": "direct"
      },
      {
        "tag": "openai_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo/geosite/openai.srs",
        "download_detour": "direct"
      },
      {
        "tag": "proxy_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo/geosite/geolocation-!cn.srs",
        "download_detour": "direct"
      },
      {
        "tag": "telegram_ip",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geoip/telegram.srs",
        "download_detour": "direct"
      },
      {
        "tag": "telegram_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/telegram.srs",
        "download_detour": "direct"
      },
      {
        "tag": "youtube_domain",
        "type": "remote",
        "format": "binary",
        "url": "https://ghfast.top/https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/sing/geo-lite/geosite/youtube.srs",
        "download_detour": "direct"
      }
    ],
    "final": "final",
    "auto_detect_interface": true
  },
  "outbounds": [
    {
      "tag": "proxy",
      "type": "selector",
      "outbounds": [
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto",
        "direct"
      ],
      "default": "all-auto"
    },
    {
      "tag": "google",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "apple",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "direct"
    },
    {
      "tag": "telegram",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "bilibili",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "direct"
    },
    {
      "tag": "netflix",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "bahamut",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "youtube",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "openai",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "cn",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "direct"
    },
    {
      "tag": "final",
      "type": "selector",
      "outbounds": [
        "proxy",
        "direct",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "proxy"
    },
    {
      "tag": "hk",
      "type": "selector",
      "outbounds": []
    },
    {
      "tag": "tw",
      "type": "selector",
      "outbounds": []
    },
    {
      "tag": "jp",
      "type": "selector",
      "outbounds": []
    },
    {
      "tag": "sg",
      "type": "selector",
      "outbounds": []
    },
    {
      "tag": "us",
      "type": "selector",
      "outbounds": []
    },
    {
      "tag": "all",
      "type": "selector",
      "outbounds": []
    },
    {
      "tag": "hk-auto",
      "type": "urltest",
      "outbounds": [],
      "url": "https://www.gstatic.com/generate_204",
      "interval": "1m",
      "tolerance": 50
    },
    {
      "tag": "tw-auto",
      "type": "urltest",
      "outbounds": [],
      "url": "https://www.gstatic.com/generate_204",
      "interval": "1m",
      "tolerance": 50
    },
    {
      "tag": "jp-auto",
      "type": "urltest",
      "outbounds": [],
      "url": "https://www.gstatic.com/generate_204",
      "interval": "1m",
      "tolerance": 50
    },
    {
      "tag": "sg-auto",
      "type": "urltest",
      "outbounds": [],
      "url": "https://www.gstatic.com/generate_204",
      "interval": "1m",
      "tolerance": 50
    },
    {
      "tag": "us-auto",
      "type": "urltest",
      "outbounds": [],
      "url": "https://www.gstatic.com/generate_204",
      "interval": "1m",
      "tolerance": 50
    },
    {
      "tag": "all-auto",
      "type": "urltest",
      "outbounds": [],
      "url": "https://www.gstatic.com/generate_204",
      "interval": "1m",
      "tolerance": 50
    },
    {
      "tag": "GLOBAL",
      "type": "selector",
      "outbounds": [
        "direct",
        "proxy",
        "hk",
        "hk-auto",
        "tw",
        "tw-auto",
        "jp",
        "jp-auto",
        "sg",
        "sg-auto",
        "us",
        "us-auto",
        "all",
        "all-auto"
      ],
      "default": "direct"
    },
    {
      "tag": "direct",
      "type": "direct"
    }
  ],
  "inbounds": [
    {
      "type": "tun",
      "address": [
        "172.19.0.0/30",
        "fdfe:dcba:9876::0/126"
      ],
      "stack": "mixed",
      "auto_route": true,
      "platform": {
        "http_proxy": {
          "enabled": true,
          "server": "127.0.0.1",
          "server_port": 7890
        }
      }
    },
    {
      "type": "mixed",
      "listen": "127.0.0.1",
      "listen_port": 7890
    }
  ],
  "experimental": {
    "clash_api": {
      "external_controller": "127.0.0.1:9090",
      "external_ui": "ui",
      "external_ui_download_url": "https://ghfast.top/https://github.com/MetaCubeX/metacubexd/archive/refs/heads/gh-pages.zip",
      "external_ui_download_detour": "direct"
    },
    "cache_file": {
      "enabled": true,
      "store_fakeip": true
    }
  },
  "log": {
    "disabled": false,
    "level": "info",
    "timestamp": true
  }
}