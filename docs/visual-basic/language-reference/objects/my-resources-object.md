---
title: "My.Resources オブジェクト"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e5b909d9945ed631cebe07e4cfc7d5dc2e019f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="myresources-object"></a><span data-ttu-id="2bc09-102">My.Resources オブジェクト</span><span class="sxs-lookup"><span data-stu-id="2bc09-102">My.Resources Object</span></span>
<span data-ttu-id="2bc09-103">アプリケーションのリソースにアクセスするには、プロパティとクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc09-104">コメント</span><span class="sxs-lookup"><span data-stu-id="2bc09-104">Remarks</span></span>  
 <span data-ttu-id="2bc09-105">`My.Resources`オブジェクトがアプリケーションのリソースへのアクセスを提供および使用すると動的にアプリケーションのリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="2bc09-106">詳細については、次を参照してください。[を管理するアプリケーションのリソース (.NET)](/visualstudio/ide/managing-application-resources-dotnet)です。</span><span class="sxs-lookup"><span data-stu-id="2bc09-106">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="2bc09-107">`My.Resources`オブジェクトはグローバル リソースのみを公開します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="2bc09-108">フォームに関連付けられているリソース ファイルへのアクセスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="2bc09-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="2bc09-109">フォームからフォーム リソースにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bc09-109">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="2bc09-110">アプリケーションのカルチャに固有のリソース ファイルにアクセスすることができます、`My.Resources`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2bc09-110">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="2bc09-111">既定では、`My.Resources`オブジェクト内のカルチャに一致するリソース ファイルからリソースを検索、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2bc09-111">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="2bc09-112">ただし、この動作をオーバーライドし、リソースを使用する特定のカルチャを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2bc09-112">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="2bc09-113">詳細については、「[デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bc09-113">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2bc09-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2bc09-114">Properties</span></span>  
 <span data-ttu-id="2bc09-115">プロパティ、`My.Resources`オブジェクトは、アプリケーションのリソースへの読み取り専用のアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-115">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="2bc09-116">追加またはリソースを削除するを使用して、**プロジェクト デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="2bc09-116">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="2bc09-117">によって追加されるリソースにアクセスすることができます、**プロジェクト デザイナー**を使用して`My.Resources.``resourceName`です。</span><span class="sxs-lookup"><span data-stu-id="2bc09-117">You can access resources added through the **Project Designer** by using `My.Resources.``resourceName`.</span></span>  
  
 <span data-ttu-id="2bc09-118">追加またはでプロジェクトを選択してリソース ファイルを削除することができますも**ソリューション エクスプ ローラー**をクリックすると、**新しい項目の追加**または**既存項目の追加**から、 **プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2bc09-118">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="2bc09-119">使用してこのような追加リソースにアクセスすることができます`My.Resources.``resourceFileName`.`resourceName`です。</span><span class="sxs-lookup"><span data-stu-id="2bc09-119">You can access resources added in this manner by using `My.Resources.``resourceFileName`.`resourceName`.</span></span>  
  
 <span data-ttu-id="2bc09-120">各リソースの名前、カテゴリ、および、値があり、これらのリソース設定でのリソースにアクセスするプロパティの表示方法を決定、`My.Resources`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2bc09-120">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="2bc09-121">追加するリソースの**プロジェクト デザイナー**:</span><span class="sxs-lookup"><span data-stu-id="2bc09-121">For resources added in the **Project Designer**:</span></span>  
  
-   <span data-ttu-id="2bc09-122">名前、プロパティの名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-122">The name determines the name of the property,</span></span>  
  
-   <span data-ttu-id="2bc09-123">リソース データは、プロパティの値</span><span class="sxs-lookup"><span data-stu-id="2bc09-123">The resource data is the value of the property,</span></span>  
  
-   <span data-ttu-id="2bc09-124">カテゴリは、プロパティの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-124">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="2bc09-125">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="2bc09-125">Category</span></span>|<span data-ttu-id="2bc09-126">プロパティのデータ型</span><span class="sxs-lookup"><span data-stu-id="2bc09-126">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="2bc09-127">**文字列**</span><span class="sxs-lookup"><span data-stu-id="2bc09-127">**Strings**</span></span>|[<span data-ttu-id="2bc09-128">String</span><span class="sxs-lookup"><span data-stu-id="2bc09-128">String</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|<span data-ttu-id="2bc09-129">**イメージ**</span><span class="sxs-lookup"><span data-stu-id="2bc09-129">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="2bc09-130">**アイコン**</span><span class="sxs-lookup"><span data-stu-id="2bc09-130">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="2bc09-131">**オーディオ**</span><span class="sxs-lookup"><span data-stu-id="2bc09-131">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="2bc09-132"><xref:System.IO.UnmanagedMemoryStream>から派生したクラス、<xref:System.IO.Stream>など、ストリームを取るメソッドで使用できるように、クラス、<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2bc09-132">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="2bc09-133">**ファイル**</span><span class="sxs-lookup"><span data-stu-id="2bc09-133">**Files**</span></span>|<span data-ttu-id="2bc09-134">-   [文字列](../../../visual-basic/language-reference/data-types/string-data-type.md)テキスト ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="2bc09-134">-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="2bc09-135">-   <xref:System.Drawing.Bitmap>イメージ ファイル。</span><span class="sxs-lookup"><span data-stu-id="2bc09-135">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="2bc09-136">-   <xref:System.Drawing.Icon>アイコン ファイルです。</span><span class="sxs-lookup"><span data-stu-id="2bc09-136">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="2bc09-137">-   <xref:System.IO.UnmanagedMemoryStream>音声ファイル。</span><span class="sxs-lookup"><span data-stu-id="2bc09-137">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="2bc09-138">**その他**</span><span class="sxs-lookup"><span data-stu-id="2bc09-138">**Other**</span></span>|<span data-ttu-id="2bc09-139">デザイナーの内の情報によって決まります**型**列です。</span><span class="sxs-lookup"><span data-stu-id="2bc09-139">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="2bc09-140">クラス</span><span class="sxs-lookup"><span data-stu-id="2bc09-140">Classes</span></span>  
 <span data-ttu-id="2bc09-141">`My.Resources`オブジェクトは、共有のプロパティを持つクラスとして各リソース ファイルを公開します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-141">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="2bc09-142">クラス名は、リソース ファイルの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="2bc09-142">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="2bc09-143">前のセクションで説明した、リソース ファイル内のリソースが、クラスのプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="2bc09-143">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bc09-144">例</span><span class="sxs-lookup"><span data-stu-id="2bc09-144">Example</span></span>  
 <span data-ttu-id="2bc09-145">この例では、という名前の文字列リソースをフォームのタイトルを設定`Form1Title`アプリケーション リソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="2bc09-145">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="2bc09-146">例が動作するには、アプリケーションが必要という名前の文字列`Form1Title`リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="2bc09-146">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="2bc09-147">例</span><span class="sxs-lookup"><span data-stu-id="2bc09-147">Example</span></span>  
 <span data-ttu-id="2bc09-148">この例は、という名前のアイコンをフォームのアイコンを設定`Form1Icon`アプリケーションのリソース ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="2bc09-148">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="2bc09-149">例が動作するには、アプリケーションが必要という名前のアイコン`Form1Icon`リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="2bc09-149">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="2bc09-150">例</span><span class="sxs-lookup"><span data-stu-id="2bc09-150">Example</span></span>  
 <span data-ttu-id="2bc09-151">この例では、という名前のイメージ リソースをフォームの背景イメージを設定`Form1Background`アプリケーションのリソース ファイルであります。</span><span class="sxs-lookup"><span data-stu-id="2bc09-151">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="2bc09-152">この例を実行するアプリケーションが必要という名前のイメージ リソース`Form1Background`リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="2bc09-152">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="2bc09-153">例</span><span class="sxs-lookup"><span data-stu-id="2bc09-153">Example</span></span>  
 <span data-ttu-id="2bc09-154">この例は、という名前のオーディオ リソースとして格納されているサウンドを再生`Form1Greeting`アプリケーションのリソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="2bc09-154">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="2bc09-155">アプリケーションの例が機能するには、名前付きオーディオ リソースがある必要があります`Form1Greeting`リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="2bc09-155">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="2bc09-156">`My.Computer.Audio.Play`メソッドは、Windows フォーム アプリケーションでのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-156">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="2bc09-157">例</span><span class="sxs-lookup"><span data-stu-id="2bc09-157">Example</span></span>  
 <span data-ttu-id="2bc09-158">この例では、アプリケーションの文字列リソースのフランス語のカルチャのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-158">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="2bc09-159">リソースが名前付き`Message`します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-159">The resource is named `Message`.</span></span> <span data-ttu-id="2bc09-160">カルチャを変更すること、`My.Resources`オブジェクトを使用して、この例では<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-160">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="2bc09-161">この例を実行するアプリケーションが必要という名前の文字列`Message`に、リソース ファイル、およびアプリケーションはがリソース ファイルで、あり用のフランス語のカルチャのバージョン。</span><span class="sxs-lookup"><span data-stu-id="2bc09-161">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="2bc09-162">アプリケーションには、リソース ファイルのフランス語のカルチャ バージョンがない場合、`My.Resource`オブジェクトは、既定のカルチャのリソース ファイルからリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="2bc09-162">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2bc09-163">参照</span><span class="sxs-lookup"><span data-stu-id="2bc09-163">See Also</span></span>  
 [<span data-ttu-id="2bc09-164">アプリケーション リソースの管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="2bc09-164">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)  
 [<span data-ttu-id="2bc09-165">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="2bc09-165">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)  

