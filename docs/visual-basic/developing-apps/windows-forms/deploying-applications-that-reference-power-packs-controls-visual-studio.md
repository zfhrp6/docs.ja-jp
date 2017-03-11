---
title: "Deploying Applications That Reference Power Packs Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Power Packs, deploying"
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Deploying Applications That Reference Power Packs Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Power Packs コントロール \(<xref:Microsoft.VisualBasic.PowerPacks.LineShape>、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>、<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>、または <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>\) を参照するアプリケーションを配置するには、配置先のコンピューターに Power Packs コントロールがインストールされている必要があります。  
  
## 必要条件としての Power Packs コントロールのインストール  
 アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。  必須コンポーネントのインストール プロセスは、*ブートストラップ*と呼ばれます。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] を開発用コンピューターにインストールするとき、Power Packs ブートストラップ パッケージが [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] ブートストラップ ディレクトリに追加されます。  その後、[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] または Windows インストーラー配置のための必要条件を追加する手順に従うと、このパッケージが使用可能になります。  
  
 既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。  または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。  
  
> [!NOTE]
>  ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。  つまり、[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] アプリケーションの場合、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールするために管理者権限が必要です。  アプリケーションのインストール後は、管理者権限がなくてもアプリケーションを実行できます。  
  
 インストール中、配置先のコンピューターに Power Packs コントロールが存在しない場合は、Power Packs コントロールをインストールするように求めるメッセージが表示されます。  
  
 ブートストラップの代わりに、Microsoft Systems Management Server などの電子ソフトウェア配布システムを使用して、Power Packs コントロールを事前に配置することもできます。  
  
## 参照  
 [How to: Install Prerequisites in Windows Installer Deployment](http://msdn.microsoft.com/ja-jp/653fc868-2486-429c-b75e-2f9d0c7f6619)   
 [方法 : ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Not in Build: Choosing a Deployment Strategy](http://msdn.microsoft.com/ja-jp/ecd632d8-063c-4028-b785-81bba045107b)   
 [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)