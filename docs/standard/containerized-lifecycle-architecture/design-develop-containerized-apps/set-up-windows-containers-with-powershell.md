---
title: DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定するには
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: d68378a12a16dd4072b381f00241e781b40c3e16
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105551"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="a4161-103">DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定するには</span><span class="sxs-lookup"><span data-stu-id="a4161-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="a4161-104">[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)、Docker イメージを既存の Windows アプリケーションに変換し、Docker エコシステムの残りの部分と同じツールを使用して配置できます。</span><span class="sxs-lookup"><span data-stu-id="a4161-104">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="a4161-105">Windows コンテナーを使用するのにするだけ、DockerFile で Windows PowerShell コマンドを記述する次の例で示したようにします。</span><span class="sxs-lookup"><span data-stu-id="a4161-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="a4161-106">ここを使用して Windows PowerShell、Windows Server Core 基本イメージと IIS をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a4161-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="a4161-107">同様の方法で使用することもでしたの Windows PowerShell コマンド、従来の ASP.NET などの追加コンポーネントを設定する 4.x および .NET 4.6、またはその他の Windows ソフトウェア、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="a4161-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="a4161-108">[前へ](visual-studio-tools-for-docker.md)
[次へ](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="a4161-108">[Previous](visual-studio-tools-for-docker.md)
[Next](../docker-devops-workflow/index.md)</span></span>
