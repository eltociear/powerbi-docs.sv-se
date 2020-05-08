---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "61194085"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Använda DAX-funktionen username() eller userprincipalname()
Du kan använda funktionerna DAX *username()* eller *userprincipalname()* i din datauppsättning. Du kan använda dem i uttryck i Power BI Desktop. När du publicerar din modell kommer den att användas i Power BI-tjänsten.

I Power BI Desktop *username()* returneras en användare i formatet *domän\användare* och *userprincipalname()* returneras en användare i formatet <em>user@contoso.com</em>.

I Power BI-tjänsten *username()* och *userprincipalname()* både returnerar användarens primära namn (User Principal Name). Detta liknar en e-postadress.

