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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 81483722227873d1b145219ae5c4326d841ff876
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="b5279-102">パッケージ化とカスタム My 拡張 (Visual Basic) の配置</span><span class="sxs-lookup"><span data-stu-id="b5279-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="b5279-103">Visual Basic では、ユーザー設定を展開するための簡単な方法`My`Visual Studio テンプレートを使用して名前空間の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b5279-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="b5279-104">プロジェクト テンプレートを作成する場合、`My`拡張機能は、新しいプロジェクトの種類の不可欠な部分、カスタムを含めるだけ`My`テンプレートをエクスポートする場合は、プロジェクトで拡張機能のコードです。</span><span class="sxs-lookup"><span data-stu-id="b5279-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="b5279-105">プロジェクト テンプレートをエクスポートする方法の詳細については、次を参照してください。[方法: プロジェクト テンプレートを作成する](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398)です。</span><span class="sxs-lookup"><span data-stu-id="b5279-105">For more information about exporting project templates, see [How to: Create Project Templates](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).</span></span>  
  
 <span data-ttu-id="b5279-106">場合は、カスタム`My`拡張機能が&1; つのコード ファイルに、ユーザーが任意の種類の Visual Basic プロジェクトに追加できる項目テンプレートとして、ファイルをエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5279-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="b5279-107">追加の機能と、カスタムの動作を有効にする項目テンプレートをカスタマイズすることができますし、 `My` Visual Basic プロジェクトで拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b5279-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="b5279-108">それらの機能を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="b5279-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="b5279-109">ユーザーに対し、カスタムの管理を許可する`My`から拡張機能、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。</span><span class="sxs-lookup"><span data-stu-id="b5279-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="b5279-110">独自の自動追加`My`指定したアセンブリへの参照時に拡張子がプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="b5279-111">非表示にする、`My`拡張項目テンプレートを**項目の追加**ダイアログ ボックスがプロジェクト項目の一覧に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="b5279-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="b5279-112">このトピックでは、カスタムのパッケージ化する方法について説明`My`から管理可能な非表示の項目テンプレートと拡張機能、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。</span><span class="sxs-lookup"><span data-stu-id="b5279-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="b5279-113">カスタム`My`拡張機能追加することも自動的に指定したアセンブリへの参照がプロジェクトに追加されるとします。</span><span class="sxs-lookup"><span data-stu-id="b5279-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="b5279-114">作成、My 名前空間の拡張機能</span><span class="sxs-lookup"><span data-stu-id="b5279-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="b5279-115">ユーザー定義の展開パッケージを作成するのには、まず`My`拡張機能は、1 つのコード ファイルとして拡張機能を作成します。</span><span class="sxs-lookup"><span data-stu-id="b5279-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="b5279-116">詳細およびカスタムを作成する方法に関するガイダンス`My`拡張機能を参照してください[Visual Basic の My Namespace を拡張する](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5279-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="b5279-117">エクスポートする項目のテンプレートと My 名前空間の拡張</span><span class="sxs-lookup"><span data-stu-id="b5279-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="b5279-118">含むコード ファイルを作成したら、`My`名前空間の拡張機能のコード ファイルを Visual Studio 項目テンプレートとしてエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5279-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="b5279-119">Visual Studio 項目テンプレートとしてファイルをエクスポートする方法については、次を参照してください。[方法: 項目テンプレートを作成する](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5)です。</span><span class="sxs-lookup"><span data-stu-id="b5279-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5279-120">場合、`My`を自動的にインストールする項目テンプレートをカスタマイズできます。 名前空間の拡張機能は、特定のアセンブリに対する依存関係を持つ、`My`そのアセンブリへの参照が追加されたときに名前空間の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b5279-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="b5279-121">その結果、コード ファイルを Visual Studio 項目テンプレートとしてエクスポートするときに、アセンブリ参照を除外するされます。</span><span class="sxs-lookup"><span data-stu-id="b5279-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="b5279-122">項目テンプレートをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="b5279-122">Customize the item template</span></span>  
 <span data-ttu-id="b5279-123">管理する項目テンプレートを有効にすることができます、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。</span><span class="sxs-lookup"><span data-stu-id="b5279-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="b5279-124">また、指定したアセンブリへの参照がプロジェクトに追加されたときに自動的に追加する項目テンプレートを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5279-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="b5279-125">これらのカスタマイズを有効にするのには、テンプレートに、CustomData ファイルと呼ばれる新しいファイルを追加され、.vstemplate ファイル内に XML に新しい要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="b5279-126">CustomData ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-126">Add the CustomData file</span></span>  
 <span data-ttu-id="b5279-127">CustomData ファイルは、ファイル名拡張子を持つテキスト ファイルです。CustomData (ファイル名できます設定する任意の値に、テンプレートに意味のある)、XML を含みます。</span><span class="sxs-lookup"><span data-stu-id="b5279-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="b5279-128">CustomData ファイル内の XML に指示を含める Visual Basic、`My`拡張機能の使用時に、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。</span><span class="sxs-lookup"><span data-stu-id="b5279-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="b5279-129">必要に応じて追加することができます、`AssemblyFullName>`属性を XML CustomData ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b5279-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="b5279-130">これにより、ユーザー設定を自動的にインストールする Visual Basic`My`特定のアセンブリへの参照時に拡張子がプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="b5279-131">CustomData ファイルを作成する任意のテキスト エディターまたは XML エディターを使用して、項目テンプレートの圧縮フォルダー (.zip ファイル) に追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="b5279-132">たとえば、次の XML では Microsoft.VisualBasic.PowerPacks.Vs.dll アセンブリへの参照時に、Visual Basic プロジェクトの My 拡張フォルダーにテンプレート項目を追加する CustomData ファイルの内容がプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="b5279-133">CustomData ファイルに含まれる、`VBMyExtensionTemplate>`を次の表に記載されている属性を持つ要素。</span><span class="sxs-lookup"><span data-stu-id="b5279-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="b5279-134">属性</span><span class="sxs-lookup"><span data-stu-id="b5279-134">Attribute</span></span>|<span data-ttu-id="b5279-135">説明</span><span class="sxs-lookup"><span data-stu-id="b5279-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="b5279-136">必須です。</span><span class="sxs-lookup"><span data-stu-id="b5279-136">Required.</span></span> <span data-ttu-id="b5279-137">拡張機能の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="b5279-137">A unique identifier for the extension.</span></span> <span data-ttu-id="b5279-138">この ID を持つ拡張機能は既にプロジェクトに追加されている場合、ユーザーは、再度追加するプロンプトされません。</span><span class="sxs-lookup"><span data-stu-id="b5279-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="b5279-139">必須です。</span><span class="sxs-lookup"><span data-stu-id="b5279-139">Required.</span></span> <span data-ttu-id="b5279-140">項目テンプレートのバージョン番号です。</span><span class="sxs-lookup"><span data-stu-id="b5279-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="b5279-141">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b5279-141">Optional.</span></span> <span data-ttu-id="b5279-142">アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="b5279-142">An assembly name.</span></span> <span data-ttu-id="b5279-143">追加するユーザーの入力を求め、このアセンブリへの参照がプロジェクトに追加されると、`My`このアイテム テンプレートからの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b5279-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="b5279-144">追加、 \<CustomDataSignature >.vstemplate ファイルの要素</span><span class="sxs-lookup"><span data-stu-id="b5279-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="b5279-145">Visual Studio 項目テンプレートを識別するために、`My`名前空間の拡張項目テンプレートの .vstemplate ファイルを変更することもあります。</span><span class="sxs-lookup"><span data-stu-id="b5279-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="b5279-146">追加する必要があります、`<CustomDataSignature>`要素を`<TemplateData>`要素。</span><span class="sxs-lookup"><span data-stu-id="b5279-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="b5279-147">`<CustomDataSignature>`要素は、テキストを含める必要があります`Microsoft.VisualBasic.MyExtension`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b5279-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="b5279-148">圧縮フォルダー (.zip ファイル) 内のファイルを直接変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b5279-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="b5279-149">.Vstemplate ファイルを圧縮フォルダーからコピーする必要があります、変更して、圧縮フォルダー内の .vstemplate ファイル、更新されたコピーを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b5279-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="b5279-150">次の例を含む .vstemplate ファイルの内容を示しています、`<CustomDataSignature>`要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="b5279-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
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
  
## <a name="install-the-template"></a><span data-ttu-id="b5279-151">テンプレートをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b5279-151">Install the template</span></span>  
 <span data-ttu-id="b5279-152">テンプレートをインストールするには、Visual Basic 項目テンプレート フォルダー (たとえば、My documents \visual Studio 2008\Templates\Item \templates\item templates \visual Basic) を圧縮フォルダー (.zip ファイル) をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="b5279-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="b5279-153">また、Visual Studio インストーラー (.vsi) ファイルとしてテンプレートを公開することができます。</span><span class="sxs-lookup"><span data-stu-id="b5279-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5279-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5279-154">See also</span></span>  
 <span data-ttu-id="b5279-155">[Visual Basic における My 名前空間の拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="b5279-155">[Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span></span>  
<span data-ttu-id="b5279-156"> [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span><span class="sxs-lookup"><span data-stu-id="b5279-156"> [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span></span>  
<span data-ttu-id="b5279-157"> [利用可能なオブジェクトのカスタマイズ ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span><span class="sxs-lookup"><span data-stu-id="b5279-157"> [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span></span>  
<span data-ttu-id="b5279-158"> [マイ拡張 ページ、プロジェクト デザイナー](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="b5279-158"> [My Extensions Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span></span>
