---
title: PrintForm コンポーネント (Visual Basic) を参照するアプリケーションの配置
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>PrintForm コンポーネント (Visual Basic) を参照するアプリケーションの配置
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを参照するアプリケーションを配置する場合は、コンポーネントをターゲット コンピューターにインストールする必要があります。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>必要条件として PrintForm をインストールする  
 アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。 必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントのインストール時に、Microsoft Visual Basic Power Packs ブートストラップ パッケージが [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ブートストラップ ディレクトリに追加されます。 その後、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] または Windows インストーラー配置のための必要条件を追加する手順に従うと、このパッケージが使用可能になります。  
  
 既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。 または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。  
  
> [!NOTE]
>  ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。 つまり、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] アプリケーションの場合、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールするために管理アクセス許可が必要です。 アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。  
  
 インストール中に、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントがターゲット コンピューター上に存在しなければ、ユーザーはこれをインストールするよう求められます。  
  
 ブートストラップの代わりに、Microsoft Systems Management Server などの電子ソフトウェア配布システムを使って <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを事前に配置することもできます。  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [PrintForm コンポーネント](../../../visual-basic/developing-apps/printing/printform-component.md)
