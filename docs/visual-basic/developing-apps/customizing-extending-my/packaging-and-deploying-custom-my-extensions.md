---
title: パッケージ化と配置カスタム My 拡張機能 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 901d0b80a18d2f4d262cc65eb485dcc628bc6a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>パッケージ化と配置カスタム My 拡張機能 (Visual Basic)
Visual Basic では、ユーザー設定を展開するための簡単な方法`My`Visual Studio テンプレートを使用して名前空間の拡張機能です。 対象のプロジェクト テンプレートを作成する場合、`My`拡張機能は、新しいプロジェクトの種類の不可欠なカスタムを含めることができますのみ`My`プロジェクト テンプレートをエクスポートするときに拡張機能のコード。 プロジェクト テンプレートのエクスポートの詳細については、次を参照してください。[する方法: プロジェクト テンプレートを作成する](/visualstudio/ide/how-to-create-project-templates)です。  
  
 場合、カスタム`My`拡張機能が 1 つのコード ファイルに、ユーザーが任意の種類の Visual Basic プロジェクトに追加できる項目テンプレートと、ファイルをエクスポートすることができます。 追加の機能と、カスタムの動作を有効にする項目テンプレートをカスタマイズすることができますし、 `My` Visual Basic プロジェクトの拡張機能です。 これらの機能を以下に示します。  
  
-   ユーザーが、カスタムの管理を許可する`My`から拡張機能、**マイ拡張**Visual Basic プロジェクト デザイナーのページです。  
  
-   独自の自動追加`My`拡張機能と、指定したアセンブリへの参照がプロジェクトに追加します。  
  
-   非表示にする、`My`で拡張機能の項目テンプレート、**項目の追加** ダイアログ ボックスのプロジェクト項目の一覧に含まれていないようにします。  
  
 カスタムのパッケージ化する方法について説明`My`拡張機能を非表示の項目テンプレートから管理できるとして、**マイ拡張**Visual Basic プロジェクト デザイナーのページです。 カスタム`My`拡張機能追加することも自動的に指定したアセンブリへの参照がプロジェクトに追加されるとします。  
  
## <a name="create-a-my-namespace-extension"></a>作成、マイ名前空間拡張  
 ユーザー定義の展開パッケージの作成の最初のステップ`My`拡張機能は、拡張機能として、1 つのコード ファイルを作成します。 詳細とカスタムを作成する方法に関するガイダンス`My`拡張機能を参照してください[Visual Basic での My Namespace を拡張する](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)です。  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>エクスポートする項目テンプレートとマイ名前空間拡張  
 含むコード ファイルを作成したら、`My`名前空間の拡張機能、コード ファイルを Visual Studio 項目テンプレートとしてエクスポートすることができます。 手順として、Visual Studio 項目テンプレート ファイルをエクスポートする方法については、次を参照してください。[する方法: 項目テンプレートを作成する](/visualstudio/ide/how-to-create-item-templates)です。  
  
> [!NOTE]
>  場合、`My`を自動的にインストールするように項目テンプレートをカスタマイズできます。 名前空間の拡張機能は、特定のアセンブリに対する依存関係を持つ、`My`名前空間拡張を、アセンブリへの参照を追加するとします。 その結果、Visual Studio 項目テンプレートと、コード ファイルをエクスポートするときに、アセンブリ参照を除外するされます。  
  
## <a name="customize-the-item-template"></a>項目テンプレートをカスタマイズします。  
 項目テンプレートから管理することができます、**マイ拡張**Visual Basic プロジェクト デザイナーのページです。 また、指定したアセンブリへの参照がプロジェクトに追加されたときに自動的に追加する項目テンプレートを有効にすることができます。 これらのカスタマイズを有効にするには、テンプレートに、CustomData ファイルと呼ばれる、新しいファイルを追加し、.vstemplate ファイル内に XML を新しい要素を追加します。  
  
### <a name="add-the-customdata-file"></a>CustomData ファイルを追加します。  
 CustomData ファイルは、ファイル名拡張子を持つテキスト ファイルです。CustomData (ファイル名設定できます任意の値をテンプレートに意味のある)、XML を含むです。 CustomData ファイル内の XML を含める Visual Basic の指示、`My`ユーザーを使用して拡張機能、**マイ拡張**Visual Basic プロジェクト デザイナーのページです。 追加することができます必要に応じて、<`AssemblyFullName>`属性を XML CustomData ファイル。 これにより、ユーザー設定を自動的にインストールする Visual Basic`My`特定のアセンブリへの参照時に拡張子がプロジェクトに追加します。 CustomData ファイルを作成する任意のテキスト エディターまたは XML エディターを使用でき、項目テンプレートの圧縮フォルダー (.zip ファイル) に追加することができます。  
  
 たとえば、次の XML では Microsoft.VisualBasic.PowerPacks.Vs.dll アセンブリへの参照時に、Visual Basic プロジェクトの My の拡張機能フォルダーにテンプレート アイテムを追加する CustomData ファイルの内容がプロジェクトに追加します。  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 CustomData ファイルを含む、<`VBMyExtensionTemplate>`を次の表に記載されている属性を持つ要素。  
  
|属性|説明|  
|---|---|  
|`ID`|必須。 拡張機能の一意の識別子。 この ID を持つ拡張機能は、プロジェクトに既に追加されている場合、ユーザーは再度追加してプロンプトされません。|  
|`Version`|必須。 項目テンプレートのバージョン番号です。|  
|`AssemblyFullName`|任意。 アセンブリ名。 ユーザーを追加するように求められますがこのアセンブリへの参照がプロジェクトに追加されると、`My`この項目テンプレートからの拡張機能です。|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>追加、 \<CustomDataSignature > 要素を .vstemplate ファイル  
 として、Visual Studio 項目テンプレートを識別する、`My`名前空間の拡張項目テンプレートの .vstemplate ファイルを変更することも必要があります。 追加する必要があります、`<CustomDataSignature>`要素を`<TemplateData>`要素。 `<CustomDataSignature>`要素は、テキストを含める必要があります`Microsoft.VisualBasic.MyExtension`の次の例に示すようにします。  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 圧縮フォルダー (.zip ファイル) 内のファイルを直接変更することはできません。 .Vstemplate ファイルを圧縮フォルダーからコピー、変更後、および、更新されたコピーでは、圧縮フォルダーで .vstemplate ファイルを置き換える必要があります。  
  
 次の例を含む .vstemplate ファイルの内容を示しています、`<CustomDataSignature>`要素が追加されます。  
  
```xml  
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
 テンプレートをインストールするには、Visual Basic 項目テンプレート フォルダー (たとえば、My documents \visual Studio 2008\Templates\Item Templates\Visual 基本)、圧縮フォルダー (.zip ファイル) をコピーできます。 また、Visual Studio インストーラー (.vsi) ファイルとしてテンプレートを公開することができます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における My 名前空間の拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [[マイ拡張] ページ、プロジェクト デザイナー](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
