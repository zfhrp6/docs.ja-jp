---
title: '方法 : 厳密な名前のバイパス機能を無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9604969ea073b07af0eca8d481f5459ee15d099
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="ca16e-102">方法 : 厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="ca16e-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="ca16e-103">.NET Framework Version 3.5 Service Pack 1 (SP1) 以降、アセンブリが完全信頼の <xref:System.AppDomain> オブジェクト (`MyComputer` ゾーンに既定の <xref:System.AppDomain> など) に読み込まれている場合は、厳密な名前の署名の検証が行われなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ca16e-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="ca16e-104">これは厳密な名前のバイパス機能と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ca16e-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="ca16e-105">完全に信頼された環境では、<xref:System.Security.Permissions.StrongNameIdentityPermission> に対する完全に信頼された署名済みアセンブリの要求は、その署名に関係なく、常に成功します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="ca16e-106">ゾーンは完全に信頼されているため、唯一の制限として、アセンブリは完全に信頼されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca16e-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="ca16e-107">このような状況では厳密な名前は決定要因ではないため、これを検証する理由はありません。</span><span class="sxs-lookup"><span data-stu-id="ca16e-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="ca16e-108">厳密な名前の署名の検証をバイパスすることで、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="ca16e-109">バイパス機能は、<xref:System.AppDomainSetup.ApplicationBase%2A> プロパティで指定されたディレクトリから完全信頼の <xref:System.AppDomain> に読み込まれ、遅延署名されていないすべての完全信頼アセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ca16e-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="ca16e-110">レジストリ キー値を設定することで、コンピューターのすべてのアプリケーションに対するバイパス機能をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ca16e-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="ca16e-111">アプリケーションの構成ファイルを使用すると、単一アプリケーションの設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ca16e-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="ca16e-112">レジストリ キーを使用して無効にされているアプリケーションでは、個別にバイパス機能を元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="ca16e-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="ca16e-113">バイパス機能をオーバーライドすると、厳密な名前が正しいかどうかだけが検証されます。<xref:System.Security.Permissions.StrongNameIdentityPermission> に対するチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="ca16e-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="ca16e-114">特定の厳密な名前を確認するには、個別にチェックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca16e-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca16e-115">厳密な名前の検証を強制する機能は、次の手順で説明するように、レジストリ キーに依存します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="ca16e-116">アプリケーションが、該当のレジストリ キーへのアクセスについてアクセス制御リスト (ACL) アクセス許可を持っていないアカウントで実行されている場合、その設定は無効となります。</span><span class="sxs-lookup"><span data-stu-id="ca16e-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="ca16e-117">ACL アクセス許可を構成し、すべてのアセンブリ用に読み取ることができるようにキーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca16e-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="ca16e-118">すべてのアプリケーションに対して厳密な名前のバイパス機能を無効にするには</span><span class="sxs-lookup"><span data-stu-id="ca16e-118">To disable the strong-name bypass feature for all applications</span></span>  
  
-   <span data-ttu-id="ca16e-119">32 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーの下に、値が 0 の `AllowStrongNameBypass` という名前のダブルワード エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
-   <span data-ttu-id="ca16e-120">64 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーと HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework キーの下に、値が 0 の `AllowStrongNameBypass` という名前のダブルワード エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="ca16e-121">単一のアプリケーションに対して厳密な名前のバイパス機能を無効にするには</span><span class="sxs-lookup"><span data-stu-id="ca16e-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1.  <span data-ttu-id="ca16e-122">アプリケーションの構成ファイルを開くか、または作成します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="ca16e-123">このファイルの詳細については、「[構成ファイルを使用してアプリを構成する方法](../../../docs/framework/configure-apps/index.md)」の「アプリケーション構成ファイル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca16e-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2.  <span data-ttu-id="ca16e-124">次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="ca16e-125">アプリケーションのバイパス機能を元に戻すには、構成ファイル設定を削除するか、属性を "true" に設定します。</span><span class="sxs-lookup"><span data-stu-id="ca16e-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca16e-126">アプリケーションに対して厳密な名前のバイパス機能の有効/無効を切り替えることができるのは、コンピューターでバイパス機能が有効になっている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="ca16e-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="ca16e-127">コンピューターでバイパス機能が無効になっている場合は、すべてのアプリケーションに対して厳密な名前が検証され、単一のアプリケーションに対する検証をバイパスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ca16e-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca16e-128">参照</span><span class="sxs-lookup"><span data-stu-id="ca16e-128">See Also</span></span>  
 [<span data-ttu-id="ca16e-129">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="ca16e-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="ca16e-130">\<bypassTrustedAppStrongNames> 要素</span><span class="sxs-lookup"><span data-stu-id="ca16e-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [<span data-ttu-id="ca16e-131">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="ca16e-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
