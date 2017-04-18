---
title: "PrintForm コンポーネント (Visual Basic) を参照するアプリケーションを展開する |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 016643329d2ee66ca5a32f155cf91e0ee137f38f
ms.lasthandoff: 03/13/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>PrintForm コンポーネント (Visual Basic) を参照するアプリケーションを展開します。
参照するアプリケーションを展開する場合、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントは、コンポーネントは、セットアップ先のコンピューターにインストールする必要があります</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>前提条件として、PrintForm をインストールします。  
 アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。 必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。  
  
 ときに、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントが開発用コンピューターにインストールされている Microsoft Visual Basic Power Packs ブートス トラップ パッケージを追加する、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]ブートス トラップ ディレクトリ</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。 このパッケージは次のいずれかの前提条件を追加する手順を実行すると使用可能になります[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]または Windows インストーラーの展開。  
  
 既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。 または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。  
  
> [!NOTE]
>  ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]アプリケーション、つまり、ユーザーに、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールする管理アクセス許可は必要があります。 アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。  
  
 インストール中に、ユーザーがインストールするように求められます、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントがセットアップ先のコンピューターに存在しない場合</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
 ブートス トラップする代わりは事前に展開する、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>Microsoft Systems Management Server のような電子ソフトウェア配布システムを使用してコンポーネント</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5)   
 [PrintForm コンポーネント](../../../visual-basic/developing-apps/printing/printform-component.md)
