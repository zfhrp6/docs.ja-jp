---
title: "パッケージ化とカスタム My 拡張 (Visual Basic) を配置 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 950592c0fb197959ce1c3cf6128093846a022709
ms.lasthandoff: 03/13/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>パッケージ化とカスタム My 拡張 (Visual Basic) の配置
Visual Basic では、ユーザー設定を展開するための簡単な方法`My`Visual Studio テンプレートを使用して名前空間の拡張機能です。 プロジェクト テンプレートを作成する場合、`My`拡張機能は、新しいプロジェクトの種類の不可欠な部分、カスタムを含めるだけ`My`テンプレートをエクスポートする場合は、プロジェクトで拡張機能のコードです。 プロジェクト テンプレートをエクスポートする方法の詳細については、次を参照してください。[方法: プロジェクト テンプレートを作成する](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398)です。  
  
 場合は、カスタム`My`拡張機能が&1; つのコード ファイルに、ユーザーが任意の種類の Visual Basic プロジェクトに追加できる項目テンプレートとして、ファイルをエクスポートすることができます。 追加の機能と、カスタムの動作を有効にする項目テンプレートをカスタマイズすることができますし、 `My` Visual Basic プロジェクトで拡張機能です。 それらの機能を以下に示します。  
  
-   ユーザーに対し、カスタムの管理を許可する`My`から拡張機能、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。  
  
-   独自の自動追加`My`指定したアセンブリへの参照時に拡張子がプロジェクトに追加します。  
  
-   非表示にする、`My`拡張項目テンプレートを**項目の追加**ダイアログ ボックスがプロジェクト項目の一覧に含まれていません。  
  
 このトピックでは、カスタムのパッケージ化する方法について説明`My`から管理可能な非表示の項目テンプレートと拡張機能、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。 カスタム`My`拡張機能追加することも自動的に指定したアセンブリへの参照がプロジェクトに追加されるとします。  
  
## <a name="create-a-my-namespace-extension"></a>作成、My 名前空間の拡張機能  
 ユーザー定義の展開パッケージを作成するのには、まず`My`拡張機能は、1 つのコード ファイルとして拡張機能を作成します。 詳細およびカスタムを作成する方法に関するガイダンス`My`拡張機能を参照してください[Visual Basic の My Namespace を拡張する](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)です。  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>エクスポートする項目のテンプレートと My 名前空間の拡張  
 含むコード ファイルを作成したら、`My`名前空間の拡張機能のコード ファイルを Visual Studio 項目テンプレートとしてエクスポートすることができます。 Visual Studio 項目テンプレートとしてファイルをエクスポートする方法については、次を参照してください。[方法: 項目テンプレートを作成する](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5)です。  
  
> [!NOTE]
>  場合、`My`を自動的にインストールする項目テンプレートをカスタマイズできます。 名前空間の拡張機能は、特定のアセンブリに対する依存関係を持つ、`My`そのアセンブリへの参照が追加されたときに名前空間の拡張機能です。 その結果、コード ファイルを Visual Studio 項目テンプレートとしてエクスポートするときに、アセンブリ参照を除外するされます。  
  
## <a name="customize-the-item-template"></a>項目テンプレートをカスタマイズします。  
 管理する項目テンプレートを有効にすることができます、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。 また、指定したアセンブリへの参照がプロジェクトに追加されたときに自動的に追加する項目テンプレートを有効にすることができます。 これらのカスタマイズを有効にするのには、テンプレートに、CustomData ファイルと呼ばれる新しいファイルを追加され、.vstemplate ファイル内に XML に新しい要素を追加します。  
  
### <a name="add-the-customdata-file"></a>CustomData ファイルを追加します。  
 CustomData ファイルは、ファイル名拡張子を持つテキスト ファイルです。CustomData (ファイル名できます設定する任意の値に、テンプレートに意味のある)、XML を含みます。 CustomData ファイル内の XML に指示を含める Visual Basic、`My`拡張機能の使用時に、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。 必要に応じて追加することができます、`AssemblyFullName>`属性を XML CustomData ファイルです。 これにより、ユーザー設定を自動的にインストールする Visual Basic`My`特定のアセンブリへの参照時に拡張子がプロジェクトに追加します。 CustomData ファイルを作成する任意のテキスト エディターまたは XML エディターを使用して、項目テンプレートの圧縮フォルダー (.zip ファイル) に追加します。  
  
 たとえば、次の XML では Microsoft.VisualBasic.PowerPacks.Vs.dll アセンブリへの参照時に、Visual Basic プロジェクトの My 拡張フォルダーにテンプレート項目を追加する CustomData ファイルの内容がプロジェクトに追加します。  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 CustomData ファイルに含まれる、`VBMyExtensionTemplate>`を次の表に記載されている属性を持つ要素。  
  
|属性|説明|  
|---|---|  
|`ID`|必須です。 拡張機能の一意の識別子。 この ID を持つ拡張機能は既にプロジェクトに追加されている場合、ユーザーは、再度追加するプロンプトされません。|  
|`Version`|必須です。 項目テンプレートのバージョン番号です。|  
|`AssemblyFullName`|省略可能です。 アセンブリ名。 追加するユーザーの入力を求め、このアセンブリへの参照がプロジェクトに追加されると、`My`このアイテム テンプレートからの拡張機能です。|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>追加、 \<CustomDataSignature >.vstemplate ファイルの要素  
 Visual Studio 項目テンプレートを識別するために、`My`名前空間の拡張項目テンプレートの .vstemplate ファイルを変更することもあります。 追加する必要があります、`<CustomDataSignature>`要素を`<TemplateData>`要素。 `<CustomDataSignature>`要素は、テキストを含める必要があります`Microsoft.VisualBasic.MyExtension`の次の例に示すようにします。  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 圧縮フォルダー (.zip ファイル) 内のファイルを直接変更することはできません。 .Vstemplate ファイルを圧縮フォルダーからコピーする必要があります、変更して、圧縮フォルダー内の .vstemplate ファイル、更新されたコピーを置き換えます。  
  
 次の例を含む .vstemplate ファイルの内容を示しています、`<CustomDataSignature>`要素を追加します。  
  
```  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a>テンプレートをインストールします。  
 テンプレートをインストールするには、Visual Basic 項目テンプレート フォルダー (たとえば、My documents \visual Studio 2008\Templates\Item \templates\item templates \visual Basic) を圧縮フォルダー (.zip ファイル) をコピーできます。 また、Visual Studio インストーラー (.vsi) ファイルとしてテンプレートを公開することができます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における My 名前空間の拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [利用可能なオブジェクトのカスタマイズ ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [マイ拡張 ページ、プロジェクト デザイナー](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
