---
title: "方法: ラッパを手動で作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5451599a5421149a7dc99ced6a42bb8220af247a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="e255f-102">方法: ラッパを手動で作成する</span><span class="sxs-lookup"><span data-stu-id="e255f-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="e255f-103">マネージ ソース コード内で COM の型を手動で宣言することにした場合、まず既存のインターフェイス定義言語 (IDL: Interface Definition Language) ファイルまたはタイプ ライブラリを用意することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e255f-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="e255f-104">IDL ファイルがないか、またはタイプ ライブラリ ファイルを生成できない場合には、マネージ宣言を作成してその結果のアセンブリをタイプ ライブラリにエクスポートすることで、COM の型をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="e255f-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="e255f-105">マネージ ソースから COM の型をシミュレートするには</span><span class="sxs-lookup"><span data-stu-id="e255f-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="e255f-106">共通言語仕様 (CLS: Common Language Specification) に準拠した言語を使用して型を宣言してからファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e255f-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="e255f-107">[タイプ ライブラリ エクスポーター (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) を使用して、その型を含むアセンブリをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="e255f-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="e255f-108">エクスポートした COM タイプ ライブラリを、COM 指向のマネージ型を宣言するための基礎として使用します。</span><span class="sxs-lookup"><span data-stu-id="e255f-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="e255f-109">ランタイム呼び出し可能ラッパー (RCW: Runtime Callable Wrapper) を作成するには</span><span class="sxs-lookup"><span data-stu-id="e255f-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="e255f-110">IDL ファイルまたはタイプ ライブラリ ファイルがあることを前提として、カスタム RCW に含めるクラスとインターフェイスを決定します。</span><span class="sxs-lookup"><span data-stu-id="e255f-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="e255f-111">アプリケーション内で直接にも間接にも使用される予定がない型がある場合は、それらを除外できます。</span><span class="sxs-lookup"><span data-stu-id="e255f-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="e255f-112">CLS 準拠言語でソース ファイルを作成し、型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="e255f-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="e255f-113">インポート変換プロセスの詳しい説明については、「[タイプ ライブラリからアセンブリへの変換の要約](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e255f-113">See [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958) for a complete description of the import conversion process.</span></span> <span data-ttu-id="e255f-114">実際には、カスタム RCW を作成する場合は、[タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) によって提供される型変換機能を手動で実行していることになります。</span><span class="sxs-lookup"><span data-stu-id="e255f-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="e255f-115">次のセクションの例では、IDL またはタイプ ライブラリ ファイル内の型と、C# コード内でそれぞれに対応する型について示します。</span><span class="sxs-lookup"><span data-stu-id="e255f-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="e255f-116">宣言が完成したら、他のマネージ ソース コードのコンパイルと同様に、このファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e255f-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="e255f-117">Tlbimp.exe でインポートする型と同様に、追加情報が必要となる場合があります。その場合には、コードに直接追加できます。</span><span class="sxs-lookup"><span data-stu-id="e255f-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="e255f-118">詳細については、「[方法 : 相互運用機能アセンブリを編集する](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e255f-118">For details, see [How to: Edit Interop Assemblies](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e255f-119">例</span><span class="sxs-lookup"><span data-stu-id="e255f-119">Example</span></span>  
 <span data-ttu-id="e255f-120">IDL に含まれる `ISATest` インターフェイスおよび `SATest` クラスの例と、C# ソース コードのそれらに対応する型を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="e255f-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="e255f-121">**IDL またはタイプ ライブラリ ファイル**</span><span class="sxs-lookup"><span data-stu-id="e255f-121">**IDL or type library file**</span></span>  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="e255f-122">**マネージ ソース コード内のラッパー**</span><span class="sxs-lookup"><span data-stu-id="e255f-122">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e255f-123">参照</span><span class="sxs-lookup"><span data-stu-id="e255f-123">See Also</span></span>  
 [<span data-ttu-id="e255f-124">ランタイム呼び出し可能ラッパーのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e255f-124">Customizing Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be)  
 [<span data-ttu-id="e255f-125">COM のデータ型</span><span class="sxs-lookup"><span data-stu-id="e255f-125">COM Data Types</span></span>](http://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061)  
 [<span data-ttu-id="e255f-126">方法: 相互運用機能アセンブリの編集</span><span class="sxs-lookup"><span data-stu-id="e255f-126">How to: Edit Interop Assemblies</span></span>](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277)  
 [<span data-ttu-id="e255f-127">タイプ ライブラリからアセンブリへの変換の要約</span><span class="sxs-lookup"><span data-stu-id="e255f-127">Type Library to Assembly Conversion Summary</span></span>](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [<span data-ttu-id="e255f-128">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="e255f-128">Tlbimp.exe (Type Library Importer)</span></span>](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="e255f-129">Tlbexp.exe (タイプ ライブラリ エクスポーター)</span><span class="sxs-lookup"><span data-stu-id="e255f-129">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
