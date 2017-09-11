---
title: "/link (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
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
ms.openlocfilehash: 71ecefc898ca37cbf7299d97518e1ce2547a58da
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="link-visual-basic"></a><span data-ttu-id="d2d02-102">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2d02-102">/link (Visual Basic)</span></span>
<span data-ttu-id="d2d02-103">コンパイラで指定したアセンブリ内の COM 型情報をコンパイル中のプロジェクトにできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d2d02-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d02-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2d02-104">Syntax</span></span>  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2d02-105">引数</span><span class="sxs-lookup"><span data-stu-id="d2d02-105">Arguments</span></span>  
  
|<span data-ttu-id="d2d02-106">用語</span><span class="sxs-lookup"><span data-stu-id="d2d02-106">Term</span></span>|<span data-ttu-id="d2d02-107">定義</span><span class="sxs-lookup"><span data-stu-id="d2d02-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="d2d02-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="d2d02-108">Required.</span></span> <span data-ttu-id="d2d02-109">アセンブリ ファイル名のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="d2d02-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="d2d02-110">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2d02-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d2d02-111">Remarks</span></span>  
 <span data-ttu-id="d2d02-112">`/link`  オプションでは、埋め込み型情報を含むアプリケーションを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-112">The `/link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="d2d02-113">アプリケーションは、ランタイム アセンブリへの参照を必要とせず、埋め込み型情報を実装するランタイム アセンブリで型を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="d2d02-114">ランタイム アセンブリのさまざまなバージョンがパブリッシュされると場合、埋め込み型情報を格納しているアプリケーションが再コンパイルすることがなく、さまざまなバージョンを操作できます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="d2d02-115">例については、次を参照してください。[チュートリアル: マネージ アセンブリからの型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="d2d02-116">使用して、`/link`オプションは、COM 相互運用機能を使用する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="d2d02-116">Using the `/link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="d2d02-117">アプリケーションが不要になったターゲット コンピューターのプライマリ相互運用機能アセンブリ (PIA) を必要とされるので、COM 型を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="d2d02-118">`/link`オプションが生成されるコンパイル済みコードに参照された相互運用機能アセンブリから COM の型情報を埋め込むコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-118">The `/link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="d2d02-119">COM の型は、CLSID (GUID) 値によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="d2d02-120">その結果、アプリケーションは、同じ CLSID 値を持つ同じ COM 型がインストールされているターゲット コンピューターで実行できます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="d2d02-121">Microsoft Office を自動化するアプリケーションは、良い例です。</span><span class="sxs-lookup"><span data-stu-id="d2d02-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="d2d02-122">通常、Office のようなアプリケーションは、異なるバージョン間で同じの CLSID 値を維持、ので、アプリケーションは時間の長いとして .NET Framework 4 以降が対象のコンピューターにインストールされているし、アプリケーションのメソッド、プロパティ、または参照先の COM 型に含まれているイベントを使用して参照先の COM 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="d2d02-123">`/link`オプションは、インターフェイス、構造、およびデリゲートを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-123">The `/link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="d2d02-124">COM クラスの埋め込みはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d2d02-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2d02-125">コードで埋め込みの COM 型のインスタンスを作成する場合は、適切なインターフェイスを使用してインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2d02-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="d2d02-126">コクラスを使用して埋め込み COM 型のインスタンスを作成しようと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="d2d02-127">設定する、`/link`でオプション[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、アセンブリ参照を追加し、設定、`Embed Interop Types`プロパティを**true**します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-127">To set the `/link` option in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="d2d02-128">既定値、`Embed Interop Types`プロパティは、 **false**します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="d2d02-129">COM アセンブリ (アセンブリ A) にリンクする場合は、別の COM アセンブリ (アセンブリ B) を参照する、また、次のいずれかが true の場合は、アセンブリ B にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2d02-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="d2d02-130">アセンブリ A から型の型から継承またはアセンブリ B のインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="d2d02-131">フィールド、プロパティ、イベント、またはアセンブリ B の戻り値の型またはパラメーターの型を持つメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d2d02-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="d2d02-132">使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を&1; つ以上のアセンブリ参照があるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-132">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="d2d02-133">ように、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)コンパイラ オプション、`/link`コンパイラ オプションの参照が頻繁に使用すると、Vbc.rsp 応答ファイルを使用して[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="d2d02-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `/link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span> <span data-ttu-id="d2d02-134">使用して、 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)コンパイラ オプションと、Vbc.rsp ファイルを使用するコンパイラしたくない場合。</span><span class="sxs-lookup"><span data-stu-id="d2d02-134">Use the [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="d2d02-135">短い形式の`/link`は`/l`です。</span><span class="sxs-lookup"><span data-stu-id="d2d02-135">The short form of `/link` is `/l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="d2d02-136">ジェネリックおよび組み込み型</span><span class="sxs-lookup"><span data-stu-id="d2d02-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="d2d02-137">次のセクションでは、相互運用機能型の埋め込みのアプリケーションでジェネリック型の使用に関する制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="d2d02-138">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2d02-138">Generic Interfaces</span></span>  
 <span data-ttu-id="d2d02-139">相互運用機能アセンブリに埋め込まれているジェネリック インターフェイスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d2d02-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="d2d02-140">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d2d02-140">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="d2d02-141">[!code-vb[VbLinkCompiler&#1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2d02-141">[!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span></span>  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="d2d02-142">ジェネリック パラメーターを持つ型</span><span class="sxs-lookup"><span data-stu-id="d2d02-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="d2d02-143">相互運用機能アセンブリから型を持つが埋め込まれているジェネリック パラメーターの種類は使用できない場合、外部のアセンブリから型であります。</span><span class="sxs-lookup"><span data-stu-id="d2d02-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="d2d02-144">この制限は、インターフェイスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="d2d02-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="d2d02-145">たとえば、<xref:Microsoft.Office.Interop.Excel.Range>インターフェイスで定義されている、<xref:Microsoft.Office.Interop.Excel>アセンブリ</xref:Microsoft.Office.Interop.Excel></xref:Microsoft.Office.Interop.Excel.Range>。</span><span class="sxs-lookup"><span data-stu-id="d2d02-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="d2d02-146">ライブラリからの相互運用機能の型を埋め込んだ場合、<xref:Microsoft.Office.Interop.Excel>アセンブリと型を持つパラメーターを持つジェネリック型を返すメソッドは、公開、<xref:Microsoft.Office.Interop.Excel.Range>インターフェイスのメソッドは、次のコード例に示すように、ジェネリック インターフェイスを返す必要がある</xref:Microsoft.Office.Interop.Excel.Range></xref:Microsoft.Office.Interop.Excel>。</span><span class="sxs-lookup"><span data-stu-id="d2d02-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 <span data-ttu-id="d2d02-147">[!code-vb[VbLinkCompiler&#2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2d02-147">[!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span></span>  
<span data-ttu-id="d2d02-148">[!code-vb[VbLinkCompiler&#3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2d02-148">[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span></span>  
<span data-ttu-id="d2d02-149">[!code-vb[VbLinkCompiler&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2d02-149">[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span></span>  
  
 <span data-ttu-id="d2d02-150">次の例では、クライアント コードを返すメソッドを呼び出すことができます、<xref:System.Collections.IList>ジェネリック インターフェイスはエラーなし</xref:System.Collections.IList>。</span><span class="sxs-lookup"><span data-stu-id="d2d02-150">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 <span data-ttu-id="d2d02-151">[!code-vb[VbLinkCompiler&#5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2d02-151">[!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2d02-152">例</span><span class="sxs-lookup"><span data-stu-id="d2d02-152">Example</span></span>  
 <span data-ttu-id="d2d02-153">次のコードは、ソース ファイルをコンパイル`OfficeApp.vb`からアセンブリを参照および`COMData1.dll`と`COMData2.dll`を生成する`OfficeApp.exe`です。</span><span class="sxs-lookup"><span data-stu-id="d2d02-153">The following code compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2d02-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2d02-154">See Also</span></span>  
 <span data-ttu-id="d2d02-155">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2d02-155">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="d2d02-156"> [チュートリアル: マネージ アセンブリから型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span><span class="sxs-lookup"><span data-stu-id="d2d02-156"> [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span></span>  
<span data-ttu-id="d2d02-157"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="d2d02-157"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="d2d02-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="d2d02-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="d2d02-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span><span class="sxs-lookup"><span data-stu-id="d2d02-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span></span>  
<span data-ttu-id="d2d02-160"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="d2d02-160"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="d2d02-161"> [COM 相互運用の概要](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span><span class="sxs-lookup"><span data-stu-id="d2d02-161"> [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span></span>
