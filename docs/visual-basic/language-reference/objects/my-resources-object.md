---
title: "My.Resources オブジェクト |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
dev_langs:
- VB
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
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
ms.openlocfilehash: 68d0ce69441f18f7a59cb84b0cf363eab9f98669
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="myresources-object"></a><span data-ttu-id="55969-102">My.Resources オブジェクト</span><span class="sxs-lookup"><span data-stu-id="55969-102">My.Resources Object</span></span>
<span data-ttu-id="55969-103">アプリケーションのリソースにアクセスするためには、プロパティとクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="55969-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55969-104">コメント</span><span class="sxs-lookup"><span data-stu-id="55969-104">Remarks</span></span>  
 <span data-ttu-id="55969-105">`My.Resources`オブジェクトがアプリケーションのリソースへのアクセスを提供しを使用すると動的にアプリケーションのリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="55969-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="55969-106">詳細については、次を参照してください。[を管理するアプリケーションのリソース (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)します。</span><span class="sxs-lookup"><span data-stu-id="55969-106">For more information, see [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="55969-107">`My.Resources`オブジェクトはグローバル リソースだけを公開します。</span><span class="sxs-lookup"><span data-stu-id="55969-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="55969-108">フォームに関連付けられているリソース ファイルへのアクセスは行いません。</span><span class="sxs-lookup"><span data-stu-id="55969-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="55969-109">フォームのフォーム リソースにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55969-109">You must access the form resources from the form.</span></span> <span data-ttu-id="55969-110">詳しくは、「[チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="55969-110">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="55969-111">アプリケーションのカルチャに固有のリソース ファイルにアクセスできる、`My.Resources`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="55969-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="55969-112">既定では、`My.Resources`オブジェクトのカルチャに対応するリソース ファイルからリソースを検索、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>プロパティ</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>。</span><span class="sxs-lookup"><span data-stu-id="55969-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="55969-113">ただし、この動作をオーバーライドし、リソースに使用する特定のカルチャを指定できます。</span><span class="sxs-lookup"><span data-stu-id="55969-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="55969-114">詳細については、次を参照してください。[デスクトップ アプリでのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)します。</span><span class="sxs-lookup"><span data-stu-id="55969-114">For more information, see [Resources in Desktop Apps](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="55969-115">プロパティ</span><span class="sxs-lookup"><span data-stu-id="55969-115">Properties</span></span>  
 <span data-ttu-id="55969-116">プロパティ、`My.Resources`オブジェクトが、アプリケーションのリソースへの読み取り専用のアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="55969-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="55969-117">追加またはリソースを削除するを使用して、**プロジェクト デザイナー**します。</span><span class="sxs-lookup"><span data-stu-id="55969-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="55969-118">詳細については、次を参照してください。[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)します。</span><span class="sxs-lookup"><span data-stu-id="55969-118">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span> <span data-ttu-id="55969-119">使用して追加のリソースにアクセスすることができます、**プロジェクト デザイナー**を使用して`My.Resources.``resourceName`します。</span><span class="sxs-lookup"><span data-stu-id="55969-119">You can access resources added through the **Project Designer** by using `My.Resources.``resourceName`.</span></span>  
  
 <span data-ttu-id="55969-120">追加またはでプロジェクトを選択してリソース ファイルを削除することも**ソリューション エクスプ ローラー**をクリックすると、**新しい項目の追加**または**既存項目の追加**から、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="55969-120">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="55969-121">使用して、この方法で追加のリソースにアクセスすることができます`My.Resources.``resourceFileName`.`resourceName`します。</span><span class="sxs-lookup"><span data-stu-id="55969-121">You can access resources added in this manner by using `My.Resources.``resourceFileName`.`resourceName`.</span></span>  
  
 <span data-ttu-id="55969-122">各リソースには、名前、カテゴリ、および値、およびこれらのリソース設定で、リソースにアクセスするプロパティの表示方法を決定する、`My.Resources`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="55969-122">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="55969-123">追加するリソースの**プロジェクト デザイナー**:</span><span class="sxs-lookup"><span data-stu-id="55969-123">For resources added in the **Project Designer**:</span></span>  
  
-   <span data-ttu-id="55969-124">名前、プロパティの名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="55969-124">The name determines the name of the property,</span></span>  
  
-   <span data-ttu-id="55969-125">リソース データは、プロパティの値</span><span class="sxs-lookup"><span data-stu-id="55969-125">The resource data is the value of the property,</span></span>  
  
-   <span data-ttu-id="55969-126">カテゴリは、プロパティの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="55969-126">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="55969-127">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="55969-127">Category</span></span>|<span data-ttu-id="55969-128">プロパティのデータ型</span><span class="sxs-lookup"><span data-stu-id="55969-128">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="55969-129">**文字列**</span><span class="sxs-lookup"><span data-stu-id="55969-129">**Strings**</span></span>|[<span data-ttu-id="55969-130">String</span><span class="sxs-lookup"><span data-stu-id="55969-130">String</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|<span data-ttu-id="55969-131">**イメージ**</span><span class="sxs-lookup"><span data-stu-id="55969-131">**Images**</span></span>|<span data-ttu-id="55969-132"><xref:System.Drawing.Bitmap></xref:System.Drawing.Bitmap></span><span class="sxs-lookup"><span data-stu-id="55969-132"><xref:System.Drawing.Bitmap></span></span>|  
|<span data-ttu-id="55969-133">**アイコン**</span><span class="sxs-lookup"><span data-stu-id="55969-133">**Icons**</span></span>|<span data-ttu-id="55969-134"><xref:System.Drawing.Icon></xref:System.Drawing.Icon></span><span class="sxs-lookup"><span data-stu-id="55969-134"><xref:System.Drawing.Icon></span></span>|  
|<span data-ttu-id="55969-135">**オーディオ**</span><span class="sxs-lookup"><span data-stu-id="55969-135">**Audio**</span></span>|<span data-ttu-id="55969-136"><xref:System.IO.UnmanagedMemoryStream></xref:System.IO.UnmanagedMemoryStream></span><span class="sxs-lookup"><span data-stu-id="55969-136"><xref:System.IO.UnmanagedMemoryStream></span></span><br /><br /> <span data-ttu-id="55969-137"><xref:System.IO.UnmanagedMemoryStream>クラスから派生する、<xref:System.IO.Stream>クラスなど、ストリームを受け取るメソッドを使用できるように、<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>メソッド</xref:Microsoft.VisualBasic.Devices.Audio.Play%2A></xref:System.IO.Stream></xref:System.IO.UnmanagedMemoryStream>。</span><span class="sxs-lookup"><span data-stu-id="55969-137">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="55969-138">**ファイル**</span><span class="sxs-lookup"><span data-stu-id="55969-138">**Files**</span></span>|<span data-ttu-id="55969-139">-   [文字列](../../../visual-basic/language-reference/data-types/string-data-type.md)テキスト ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-139">-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="55969-140">-<xref:System.Drawing.Bitmap>の画像ファイル</xref:System.Drawing.Bitmap>。</span><span class="sxs-lookup"><span data-stu-id="55969-140">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="55969-141">-<xref:System.Drawing.Icon>アイコン ファイル</xref:System.Drawing.Icon>。</span><span class="sxs-lookup"><span data-stu-id="55969-141">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="55969-142">-<xref:System.IO.UnmanagedMemoryStream>のサウンド ファイル</xref:System.IO.UnmanagedMemoryStream>。</span><span class="sxs-lookup"><span data-stu-id="55969-142">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="55969-143">**その他**</span><span class="sxs-lookup"><span data-stu-id="55969-143">**Other**</span></span>|<span data-ttu-id="55969-144">デザイナーの情報によって判断**型**列です。</span><span class="sxs-lookup"><span data-stu-id="55969-144">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="55969-145">クラス</span><span class="sxs-lookup"><span data-stu-id="55969-145">Classes</span></span>  
 <span data-ttu-id="55969-146">`My.Resources`オブジェクトは各リソース ファイルを共有のプロパティを持つクラスとして公開します。</span><span class="sxs-lookup"><span data-stu-id="55969-146">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="55969-147">クラス名は、リソース ファイルの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="55969-147">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="55969-148">前のセクションで説明したように、リソース ファイル内のリソースは、クラスのプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="55969-148">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55969-149">例</span><span class="sxs-lookup"><span data-stu-id="55969-149">Example</span></span>  
 <span data-ttu-id="55969-150">この例では、フォームのタイトルを設定するという名前の文字列リソース`Form1Title`アプリケーションのリソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-150">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="55969-151">例を実行するには、アプリケーションが必要という名前の文字列`Form1Title`リソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-151">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span> <span data-ttu-id="55969-152">詳細については、次を参照してください。[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)します。</span><span class="sxs-lookup"><span data-stu-id="55969-152">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span>  
  
 <span data-ttu-id="55969-153">[!code-vb[VbVbalrMyResources&#1;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="55969-153">[!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="55969-154">例</span><span class="sxs-lookup"><span data-stu-id="55969-154">Example</span></span>  
 <span data-ttu-id="55969-155">この例では、フォームのアイコンを設定するという名前のアイコン`Form1Icon`アプリケーションのリソース ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="55969-155">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="55969-156">例を実行するには、アプリケーションが必要という名前のアイコン`Form1Icon`リソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-156">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 <span data-ttu-id="55969-157">[!code-vb[VbVbalrMyResources&#2;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="55969-157">[!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="55969-158">例</span><span class="sxs-lookup"><span data-stu-id="55969-158">Example</span></span>  
 <span data-ttu-id="55969-159">この例では、フォームの背景イメージを設定という名前のイメージ リソースを`Form1Background`がアプリケーションのリソース ファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="55969-159">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="55969-160">この例を実行するには、アプリケーションが必要という名前のイメージ リソース`Form1Background`リソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-160">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 <span data-ttu-id="55969-161">[!code-vb[VbVbalrMyResources&#3;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="55969-161">[!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="55969-162">例</span><span class="sxs-lookup"><span data-stu-id="55969-162">Example</span></span>  
 <span data-ttu-id="55969-163">この例は、名前付きオーディオ リソースとして格納されているサウンドを再生`Form1Greeting`アプリケーションのリソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-163">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="55969-164">例を実行するには、アプリケーションが必要というオーディオ リソース`Form1Greeting`リソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="55969-164">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="55969-165">`My.Computer.Audio.Play`メソッドは、Windows フォーム アプリケーションでのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="55969-165">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 <span data-ttu-id="55969-166">[!code-vb[VbVbalrMyResources&4;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="55969-166">[!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="55969-167">例</span><span class="sxs-lookup"><span data-stu-id="55969-167">Example</span></span>  
 <span data-ttu-id="55969-168">この例では、アプリケーションの文字列リソースのフランス語のカルチャのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="55969-168">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="55969-169">リソースが名前付き`Message`です。</span><span class="sxs-lookup"><span data-stu-id="55969-169">The resource is named `Message`.</span></span> <span data-ttu-id="55969-170">カルチャを変更すること、`My.Resources`オブジェクトを使用して、 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>の例</span><span class="sxs-lookup"><span data-stu-id="55969-170">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="55969-171">この例を実行するには、アプリケーションが必要という名前の文字列`Message`でのリソース ファイル、およびアプリケーションが必要にあり用、そのリソース ファイルのフランス語のカルチャのバージョン。</span><span class="sxs-lookup"><span data-stu-id="55969-171">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="55969-172">詳細については、次を参照してください。[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)します。</span><span class="sxs-lookup"><span data-stu-id="55969-172">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span> <span data-ttu-id="55969-173">アプリケーションには、リソース ファイルのフランス語のカルチャのバージョンがない場合、`My.Resource`オブジェクトは、既定のカルチャ リソース ファイルからリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="55969-173">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 <span data-ttu-id="55969-174">[!code-vb[VbVbalrMyResources&#10;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="55969-174">[!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55969-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="55969-175">See Also</span></span>  
 <span data-ttu-id="55969-176">[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d) </span><span class="sxs-lookup"><span data-stu-id="55969-176">[How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d) </span></span>  
<span data-ttu-id="55969-177"> [アプリケーションのリソース (.NET) の管理](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet) </span><span class="sxs-lookup"><span data-stu-id="55969-177"> [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet) </span></span>  
<span data-ttu-id="55969-178"> [デスクトップ アプリでのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890) </span><span class="sxs-lookup"><span data-stu-id="55969-178"> [Resources in Desktop Apps](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890) </span></span>  
<span data-ttu-id="55969-179"> [チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)</span><span class="sxs-lookup"><span data-stu-id="55969-179"> [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)</span></span>
