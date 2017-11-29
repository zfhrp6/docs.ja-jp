---
title: "Power Packs コントロール (Visual Studio) を参照するアプリケーションの配置"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Power Packs コントロール (Visual Studio) を参照するアプリケーションの配置
Power Packs コントロールを参照するアプリケーションを展開するかどうか (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>、 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>、 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>、または<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)、展開先コンピューターに、コントロールをインストールする必要があります。  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>前提条件として Power Packs コントロールをインストールします。  
 アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。 必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。  
  
 ときに[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開発用コンピューター上、ブートス トラップ パッケージに追加 Power Pack がインストールされている、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]ブートス トラップ ディレクトリ。 その後、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] または Windows インストーラー配置のための必要条件を追加する手順に従うと、このパッケージが使用可能になります。  
  
 既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。 または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。  
  
> [!NOTE]
>  ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。 つまり、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] アプリケーションの場合、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールするために管理アクセス許可が必要です。 アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。  
  
 インストール中には、展開先コンピューターに存在しない場合は、Power Packs コントロールをインストールするユーザーが求められます。  
  
 ブートス トラップする代わりには、事前に Microsoft Systems Management Server などの電子ソフトウェア配布システムを使用して Power Packs コントロールを展開することができます。  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Visual Basic Power Packs コントロール](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
