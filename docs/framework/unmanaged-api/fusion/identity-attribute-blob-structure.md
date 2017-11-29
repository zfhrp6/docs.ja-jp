---
title: "IDENTITY_ATTRIBUTE_BLOB 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: IDENTITY_ATTRIBUTE_BLOB
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords: IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b6d732f94eaa1e6988273d947ec924acf7b2521
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="identityattributeblob-structure"></a><span data-ttu-id="dfa20-102">IDENTITY_ATTRIBUTE_BLOB 構造体</span><span class="sxs-lookup"><span data-stu-id="dfa20-102">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>
<span data-ttu-id="dfa20-103">アセンブリでは、1 つの属性に関する情報が含まれておりは、3 つの`DWORD`s。</span><span class="sxs-lookup"><span data-stu-id="dfa20-103">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="dfa20-104">各`DWORD`によって生成される文字バッファーへのオフセットです、`CurrentIntoBuffer`のメソッド、 [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfa20-104">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa20-105">構文</span><span class="sxs-lookup"><span data-stu-id="dfa20-105">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="dfa20-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dfa20-106">Members</span></span>  
  
|<span data-ttu-id="dfa20-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="dfa20-107">Member</span></span>|<span data-ttu-id="dfa20-108">説明</span><span class="sxs-lookup"><span data-stu-id="dfa20-108">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="dfa20-109">最初の文字バッファーにオフセットします。</span><span class="sxs-lookup"><span data-stu-id="dfa20-109">The first offset into the character buffer.</span></span> <span data-ttu-id="dfa20-110">属性の名前空間ではなく、一連の null 文字は、このオフセットは追跡されません。</span><span class="sxs-lookup"><span data-stu-id="dfa20-110">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="dfa20-111">したがっては使用されません。</span><span class="sxs-lookup"><span data-stu-id="dfa20-111">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="dfa20-112">文字バッファーに 2 つ目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="dfa20-112">The second offset into the character buffer.</span></span> <span data-ttu-id="dfa20-113">この場所は、属性の名前の先頭をマークします。</span><span class="sxs-lookup"><span data-stu-id="dfa20-113">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="dfa20-114">文字バッファーに 3 つ目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="dfa20-114">The third offset into the character buffer.</span></span> <span data-ttu-id="dfa20-115">この場所は、属性の値の開始をマークします。</span><span class="sxs-lookup"><span data-stu-id="dfa20-115">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="dfa20-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="dfa20-116">Sample</span></span>  
 <span data-ttu-id="dfa20-117">次の例は、最終的に設定されているいくつかの基本的な手順を示しています。`IDENTITY_ATTRIBUTE_BLOB`構造体。</span><span class="sxs-lookup"><span data-stu-id="dfa20-117">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1.  <span data-ttu-id="dfa20-118">取得、 [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)アセンブリのです。</span><span class="sxs-lookup"><span data-stu-id="dfa20-118">Obtain an [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2.  <span data-ttu-id="dfa20-119">呼び出す、`IReferenceIdentity::EnumAttributes`メソッドを取得し、 [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="dfa20-119">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md).</span></span>  
  
3.  <span data-ttu-id="dfa20-120">文字バッファーを作成し、としてキャスト、`IDENTITY_ATTRIBUTE_BLOB`構造体。</span><span class="sxs-lookup"><span data-stu-id="dfa20-120">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4.  <span data-ttu-id="dfa20-121">呼び出す、`CurrentIntoBuffer`のメソッド、`IEnumIDENTITY_ATTRIBUTE`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="dfa20-121">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="dfa20-122">このメソッドは、属性、コピー `Namespace`、 `Name`、および`Value`文字バッファーにします。</span><span class="sxs-lookup"><span data-stu-id="dfa20-122">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="dfa20-123">これらの文字列に 3 つのオフセットが利用可能になる、`IDENTITY_ATTRIBUTE_BLOB`構造体。</span><span class="sxs-lookup"><span data-stu-id="dfa20-123">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||   
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity   
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;     
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],   
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",   
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),   
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =   
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed   
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =   
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="dfa20-124">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="dfa20-124">To run the sample</span></span>  
 <span data-ttu-id="dfa20-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="dfa20-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="dfa20-126">出力例</span><span class="sxs-lookup"><span data-stu-id="dfa20-126">Sample output</span></span>  
 <span data-ttu-id="dfa20-127">カルチャ ニュートラルを =</span><span class="sxs-lookup"><span data-stu-id="dfa20-127">Culture = neutral</span></span>  
  
 <span data-ttu-id="dfa20-128">名前 = システム</span><span class="sxs-lookup"><span data-stu-id="dfa20-128">name = System</span></span>  
  
 <span data-ttu-id="dfa20-129">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="dfa20-129">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="dfa20-130">PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="dfa20-130">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="dfa20-131">バージョン 2.0.0.0 を =</span><span class="sxs-lookup"><span data-stu-id="dfa20-131">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa20-132">要件</span><span class="sxs-lookup"><span data-stu-id="dfa20-132">Requirements</span></span>  
 <span data-ttu-id="dfa20-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dfa20-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa20-134">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="dfa20-134">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dfa20-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa20-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa20-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfa20-136">See Also</span></span>  
 [<span data-ttu-id="dfa20-137">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfa20-137">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 [<span data-ttu-id="dfa20-138">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfa20-138">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 [<span data-ttu-id="dfa20-139">IDENTITY_ATTRIBUTE 構造体</span><span class="sxs-lookup"><span data-stu-id="dfa20-139">IDENTITY_ATTRIBUTE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-structure.md)  
 [<span data-ttu-id="dfa20-140">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="dfa20-140">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
