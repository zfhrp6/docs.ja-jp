---
title: "マネージ コードでのプロトタイプの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a85da0d1714c263b446c88b7c18e934817aea94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="74d95-102">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="74d95-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="74d95-103">このトピックは、アンマネージ関数にアクセスする方法について説明し、マネージ コードでメソッドの定義の注釈を設定するいくつかの属性フィールドを紹介しています。</span><span class="sxs-lookup"><span data-stu-id="74d95-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="74d95-104">プラットフォーム呼び出しで使用する .NET ベースの宣言を作成する方法を示す例については、「[プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74d95-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="74d95-105">マネージ コードからアンマネージ DLL 関数にアクセスする前に、関数の名前とエクスポートする DLL の名前を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="74d95-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="74d95-106">この情報を使用すると、マネージ DLL に実装されているアンマネージ関数の定義の作成を開始できます。</span><span class="sxs-lookup"><span data-stu-id="74d95-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="74d95-107">さらに、プラットフォーム呼び出しが関数を作成し、関数間でデータをマーシャリングする方法を調整できます。</span><span class="sxs-lookup"><span data-stu-id="74d95-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74d95-108">文字列を割り当てる Win32 API 関数を使用して、`LocalFree` などのメソッドを使用して文字列を解放できます。</span><span class="sxs-lookup"><span data-stu-id="74d95-108">Win32 API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="74d95-109">プラットフォーム呼び出しは、このようなパラメーターを異なる方法で処理します。</span><span class="sxs-lookup"><span data-stu-id="74d95-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="74d95-110">プラットフォーム呼び出しでは、パラメーターを `String` 型の代わりに `IntPtr` 型にします。</span><span class="sxs-lookup"><span data-stu-id="74d95-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="74d95-111"><xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> クラスにより提供されるメソッドを使用して、型を手動で文字列に変換し、手動で解放します。</span><span class="sxs-lookup"><span data-stu-id="74d95-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="74d95-112">宣言の基本</span><span class="sxs-lookup"><span data-stu-id="74d95-112">Declaration Basics</span></span>  
 <span data-ttu-id="74d95-113">アンマネージ関数に対するマネージ定義は、次の例で確認できるように、言語に依存します。</span><span class="sxs-lookup"><span data-stu-id="74d95-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="74d95-114">完全なコード例については、「[プラットフォーム呼び出しの例](../../../docs/framework/interop/platform-invoke-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74d95-114">For more complete code examples, see [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 <span data-ttu-id="74d95-115"><xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>、<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>、<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>、<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>、<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>、または <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> の各フィールドを [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] 宣言に適用するには、`Declare` ステートメントの代わりに <xref:System.Runtime.InteropServices.DllImportAttribute> 属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74d95-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="74d95-116">定義の調整</span><span class="sxs-lookup"><span data-stu-id="74d95-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="74d95-117">明示的に設定するかどうかに関係なく、属性フィールドは作業はマネージ コードの動作を動作中に定義します。</span><span class="sxs-lookup"><span data-stu-id="74d95-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="74d95-118">プラットフォーム呼び出しは、アセンブリ内のメタデータとして存在するさまざまなフィールドで設定された既定値どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="74d95-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="74d95-119">1 つまたは複数のフィールドの値を調整することによって、この既定の動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="74d95-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="74d95-120">多くの場合、<xref:System.Runtime.InteropServices.DllImportAttribute> を使用して値を設定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="74d95-121">次の表では、プラットフォーム呼び出しに関連する属性フィールドの完全なセットを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="74d95-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="74d95-122">各フィールドについては、表に既定値とこれらのフィールドを使用してアンマネージ DLL 関数を定義する方法に関する情報へのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="74d95-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="74d95-123">フィールド</span><span class="sxs-lookup"><span data-stu-id="74d95-123">Field</span></span>|<span data-ttu-id="74d95-124">説明</span><span class="sxs-lookup"><span data-stu-id="74d95-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="74d95-125">最適なマッピングを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="74d95-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="74d95-126">メソッドの引数を渡すときに使用する呼び出し規則を指定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="74d95-127">既定値は `WinAPI` で、32 ビットの Intel ベース プラットフォームの `__stdcall` に対応します。</span><span class="sxs-lookup"><span data-stu-id="74d95-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="74d95-128">名前修飾および文字列の引数を関数にマーシャリングする方法を管理します。</span><span class="sxs-lookup"><span data-stu-id="74d95-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="74d95-129">既定値は、`CharSet.Ansi` です。</span><span class="sxs-lookup"><span data-stu-id="74d95-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="74d95-130">呼び出される DLL エントリ ポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="74d95-131">文字セットに対応するエントリ ポイントを変更する必要があるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="74d95-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="74d95-132">既定値は、プログラミング言語によって異なります。</span><span class="sxs-lookup"><span data-stu-id="74d95-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="74d95-133">マネージ メソッドのシグネチャが、HRESULT を返すアンマネージ シグネチャに変換され、戻り値の追加の [out, retval] 引数を持つかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="74d95-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="74d95-134">既定値は `true` です (シグネチャは変換されません)。</span><span class="sxs-lookup"><span data-stu-id="74d95-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="74d95-135">呼び出し元が `Marshal.GetLastWin32Error` API の関数を使用して、メソッドの実行中にエラーが発生したかどうかを判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="74d95-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="74d95-136">Visual Basic では既定値は `true`、C# および C++ では既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="74d95-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="74d95-137">ANSI の"?" 文字に変換されるマップできない Unicode 文字での例外のスローを制御します。</span><span class="sxs-lookup"><span data-stu-id="74d95-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="74d95-138">詳細なリファレンス情報については、「<xref:System.Runtime.InteropServices.DllImportAttribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74d95-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="74d95-139">プラットフォーム呼び出しのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="74d95-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="74d95-140"><xref:System.Security.Permissions.SecurityAction> 列挙型の `Assert`、`Deny`、および `PermitOnly` のメンバーは、*スタック ウォーク修飾子*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="74d95-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="74d95-141">プラットフォーム呼び出しの宣言および COM インターフェイス定義言語 (IDL) ステートメントの宣言属性として使用される場合、これらのメンバーは無視されます。</span><span class="sxs-lookup"><span data-stu-id="74d95-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="74d95-142">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="74d95-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="74d95-143">このセクションのプラットフォーム呼び出しのサンプルは、`RegistryPermission` スタック ウォーク修飾子を持つ属性の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="74d95-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="74d95-144">次のコード例では、<xref:System.Security.Permissions.SecurityAction>`Assert`、`Deny`、および `PermitOnly` 修飾子は無視されます。</span><span class="sxs-lookup"><span data-stu-id="74d95-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="74d95-145">ただし、次の例の `Demand` 修飾子は受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="74d95-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="74d95-146">プラットフォーム呼び出しを含む (ラップする) クラスに配置されている場合、<xref:System.Security.Permissions.SecurityAction> 修飾子は正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="74d95-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="74d95-147"><xref:System.Security.Permissions.SecurityAction> 修飾子は、プラットフォーム呼び出しの呼び出し元に配置されたネストしたシナリオでも正しく動作します。</span><span class="sxs-lookup"><span data-stu-id="74d95-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="74d95-148">COM 相互運用機能の例</span><span class="sxs-lookup"><span data-stu-id="74d95-148">COM Interop Examples</span></span>  
 <span data-ttu-id="74d95-149">このセクションの次の COM 相互運用機能の例は、スタック ウォーク修飾子を持つ `RegistryPermission` 属性の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="74d95-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="74d95-150">次の COM 相互運用機能のインターフェイスの宣言は、前のセクションのプラットフォーム呼び出しの例と同様に、`Assert`、`Deny`、および `PermitOnly` の修飾子を無視します。</span><span class="sxs-lookup"><span data-stu-id="74d95-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="74d95-151">さらに、次の例に示すように、`Demand` 修飾子は COM 相互運用機能のインターフェイスの宣言のシナリオでは許可されません。</span><span class="sxs-lookup"><span data-stu-id="74d95-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="74d95-152">参照</span><span class="sxs-lookup"><span data-stu-id="74d95-152">See Also</span></span>  
 [<span data-ttu-id="74d95-153">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="74d95-153">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="74d95-154">エントリ ポイントの指定</span><span class="sxs-lookup"><span data-stu-id="74d95-154">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="74d95-155">文字セットの指定</span><span class="sxs-lookup"><span data-stu-id="74d95-155">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)  
 [<span data-ttu-id="74d95-156">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="74d95-156">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="74d95-157">プラットフォーム呼び出しのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="74d95-157">Platform Invoke Security Considerations</span></span>](http://msdn.microsoft.com/en-us/bbcc67f7-50b5-4917-88ed-cb15470409fb)  
 [<span data-ttu-id="74d95-158">DLL 内の関数の識別</span><span class="sxs-lookup"><span data-stu-id="74d95-158">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="74d95-159">DLL 関数を保持するクラスの作成</span><span class="sxs-lookup"><span data-stu-id="74d95-159">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="74d95-160">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="74d95-160">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
