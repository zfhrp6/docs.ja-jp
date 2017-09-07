---
title: "Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール"
description: "Windows 10、Windows 8.1、および Windows 8 に .NET Framework 3.5 をインストールする方法について説明します"
author: rlander
ms.author: mairaw
keywords: ".Net Framework, インストール"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.translationtype: HT
ms.sourcegitcommit: 21c6a1485f3d0c38bde065d6ecc7b07d5e424c1d
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/05/2017

---

# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール

Windows 10、Windows 8.1、および Windows 8 上でアプリケーションを実行するために、.NET Framework 3.5 が必要になることがあります。 また、さらに古いバージョンの Windows にもこれらの手順を使用することもできます。

## <a name="install-the-net-framework-35-on-demand"></a>必要に応じて .NET Framework 3.5 をインストールする

.NET Framework 3.5 が必要なアプリケーションを実行しようとすると、次の構成ダイアログが表示されることがあります。 .NET Framework 3.5 を有効にするには、**[この機能をインストールする]** を選択します。 このオプションを使用するには、インターネット接続が必要です。

![.NET Framework のインストール ダイアログ](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>コントロール パネルで .NET Framework 3.5 を有効にする

Windows のコントロール パネルを使用して .NET Framework 3.5 を有効にできます。 このオプションを使用するには、インターネット接続が必要です。

1. キーボードの Windows キー ![Windows ロゴ](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) を押し、「Windows の機能」と入力して、Enter キーを押します。 **[Windows 機能の有効化または無効化]** ダイアログ ボックスが表示されます。

2. **[.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)]** チェック ボックスをオンにして **[OK]** を選択し、メッセージが表示された場合はコンピューターを再起動します。

   ![コントロール パネルを使用した .NET のインストール](./media/dotnet-control-panel.png)

   Windows Communication Foundation (WCF) 機能が必要な開発者またはサーバー管理者でない限り、**[Windows Communication Foundation HTTP アクティブ化]** および **[Windows Communication Foundation 非 HTTP アクティブ化]**の子項目を選択する必要はありません。

