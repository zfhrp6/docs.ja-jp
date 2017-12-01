---
title: "DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定するには"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: f7e92b0f1c749e2c00e3afc4ffcfc2fc88d7628f
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2017
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定するには

[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)、Docker イメージを既存の Windows アプリケーションに変換し、Docker エコシステムの残りの部分と同じツールを使用して配置できます。

Windows コンテナーを使用するのにするだけ、DockerFile で Windows PowerShell コマンドを記述する次の例で示したようにします。

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

ここを使用して Windows PowerShell、Windows Server Core 基本イメージと IIS をインストールします。

同様の方法で使用することもでしたの Windows PowerShell コマンド、従来の ASP.NET などの追加コンポーネントを設定する 4.x および .NET 4.6、またはその他の Windows ソフトウェア、次のようにします。

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
[前](visual-studio のツールでの-docker.md) [次へ] (../docker-devops-workflow/index.md)
