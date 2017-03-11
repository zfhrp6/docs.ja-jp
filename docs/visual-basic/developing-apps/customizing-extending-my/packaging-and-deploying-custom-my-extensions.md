---
title: "Packaging and Deploying Custom My Extensions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
  - "My namespace, extending"
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Packaging and Deploying Custom My Extensions (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic には、Visual Studio テンプレートを使用して、カスタムの `My` Namespace 拡張を簡単に配置できる方法が用意されています。  `My` 拡張が新しいプロジェクトの種類の不可欠な部分となるプロジェクト テンプレートを作成している場合は、テンプレートをエクスポートするときに、プロジェクトにカスタム `My` 拡張コードを含めるだけです。  プロジェクト テンプレートをエクスポートする方法の詳細については、「[方法 : プロジェクト テンプレートを作成する](../Topic/How%20to:%20Create%20Project%20Templates.md)」を参照してください。  
  
 カスタム `My` 拡張が 1 つのコード ファイルに入っている場合は、そのファイルを項目テンプレートとしてエクスポートすることで、これを任意の種類の Visual Basic プロジェクトに追加できるようになります。  項目テンプレートをカスタマイズすると、Visual Basic プロジェクト内のカスタム `My` 拡張で追加の機能や動作を有効にできます。  これには、次のような機能があります。  
  
-   Visual Basic プロジェクト デザイナーの **\[マイ拡張\]** から、ユーザーがカスタム `My` 拡張を管理できるようにする。  
  
-   特定のアセンブリへの参照がプロジェクトに追加されたときに、カスタム `My` 拡張を自動的に追加する。  
  
-   `My` 拡張の項目テンプレートを **\[項目の追加\]** ダイアログ ボックスで非表示にし、プロジェクト項目の一覧に含めないようにする。  
  
 このトピックでは、カスタム `My` 拡張を、Visual Basic のプロジェクト デザイナーの **\[マイ拡張\]** ページから管理できる非表示の項目テンプレートとしてパッケージ化する方法について説明します。  特定のアセンブリへの参照がプロジェクトに追加されたときに、カスタム `My` 拡張を自動的に追加することもできます。  
  
## My Namespace 拡張の作成  
 カスタム `My` 拡張に配置パッケージを作成する最初の手順は、拡張を 1 つのコード ファイルとして作成することです。  カスタム `My` 拡張の作成方法の詳細とガイダンスについては、「[Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)」を参照してください。  
  
## My Namespace 拡張の項目テンプレートとしてのエクスポート  
 `My` Namespace 拡張を含むコード ファイルが完成したら、そのコード ファイルを Visual Studio の項目テンプレートとしてエクスポートできます。  ファイルを Visual Studio の項目テンプレートとしてエクスポートする方法の詳細については、「[方法 : 項目テンプレートを作成する](../Topic/How%20to:%20Create%20Item%20Templates.md)」を参照してください。  
  
> [!NOTE]
>  `My` Namespace 拡張が特定のアセンブリに依存する場合は、そのアセンブリへの参照が追加されたときに、自動的に `My` Namespace 拡張をインストールするように項目テンプレートをカスタマイズできます。  このようにする場合は、コード ファイルを Visual Studio の項目テンプレートとしてエクスポートするときにアセンブリ参照を除外できます。  
  
## 項目テンプレートのカスタマイズ  
 作成した項目テンプレートは、Visual Basic プロジェクト デザイナーの **\[マイ拡張\]** ページから管理するようにできます。  また、特定のアセンブリへの参照がプロジェクトに追加されたときに、自動的に項目テンプレートが追加されるようにすることもできます。  これらのカスタマイズを有効にするには、CustomData ファイルという新しいファイルをテンプレートに追加してから、.vstemplate ファイルの XML に新しい要素を追加します。  
  
### CustomData ファイルの追加  
 CustomData ファイルは、.CustomData というファイル名拡張子を持ち、XML を含むテキスト ファイルです \(ファイル名は、テンプレートにふさわしい任意の値に設定できます\)。  CustomData ファイルの XML は、ユーザーが Visual Basic プロジェクト デザイナーの **\[マイ拡張\]** ページを使用するときに、作成した `My` 拡張を含めるように Visual Basic に指示します。  オプションで、CustomData ファイルの XML に `AssemblyFullName` 属性を追加できます。  これにより、特定のアセンブリへの参照がプロジェクトに追加されたときに、カスタム `My` 拡張を自動的にインストールするように Visual Basic に指示します。  CustomData ファイルは任意のテキスト エディターまたは XML エディターを使用して作成でき、項目テンプレートの圧縮フォルダー \(.zip ファイル\) に追加できます。  
  
 たとえば、次の XML は、Microsoft.VisualBasic.PowerPacks.Vs.dll アセンブリへの参照がプロジェクトに追加されたときに、Visual Basic プロジェクトの My Extensions フォルダーにテンプレート項目を追加する CustomData ファイルの内容を示しています。  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 この CustomData ファイルには、次の表に示す属性を持つ `VBMyExtensionTemplate` 要素が含まれています。  
  
|||  
|-|-|  
|属性|Description|  
|`ID`|必ず指定します。  拡張の一意識別子です。  この ID を持つ拡張が既にプロジェクトに追加されている場合、もう一度追加するように要求されることはありません。|  
|`Version`|必ず指定します。  項目テンプレートのバージョン番号です。|  
|`AssemblyFullName`|省略可能です。  アセンブリ名を指定します。  このアセンブリへの参照がプロジェクトに追加されると、この項目テンプレートから `My` 拡張を追加するように求めるメッセージが表示されます。|  
  
### .vstemplate ファイルへの \<CustomDataSignature\> 要素の追加  
 Visual Studio 項目テンプレートを `My` Namespace 拡張として識別するには、項目テンプレートの .vstemplate ファイルも変更する必要があります。  `<TemplateData>` 要素に `<CustomDataSignature>` 要素を追加する必要があります。  `<CustomDataSignature>` 要素には、次の例に示すように、`Microsoft.VisualBasic.MyExtension` というテキストが含まれている必要があります。  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 圧縮フォルダー \(.zip ファイル\) の中のファイルを直接変更することはできません。  圧縮フォルダーから .vstemplate ファイルをコピーして変更した後で、圧縮フォルダーの .vstemplate ファイルを更新済みのコピーと置き換える必要があります。  
  
 次の例は、`<CustomDataSignature>` 要素が追加された .vstemplate ファイルの内容を示しています。  
  
```  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature       >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
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
  
## テンプレートのインストール  
 テンプレートをインストールするには、圧縮フォルダー \(.zip ファイル\) を Visual Basic の項目テンプレート フォルダー \(My Documents\\Visual Studio 2008\\Templates\\Item Templates\\Visual Basic など\) にコピーします。  または、テンプレートを Visual Studio インストーラー \(.vsi\) ファイルとして公開することもできます。  テンプレートを Visual Studio インストーラー ファイルとして発行する方法の詳細については、「[NIB: How to: Publish Project Templates](http://msdn.microsoft.com/ja-jp/b9087f58-64e9-4767-bf54-e3bf40d63b20)」を参照してください。  
  
## 参照  
 [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [\[マイ拡張\] ページ \(プロジェクト デザイナー\)](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)