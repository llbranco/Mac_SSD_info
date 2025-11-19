# Mac_SSD_info
(WIP) Conjunto de informações sobre qual MAC usa qual modelo de SSD SATA/NVMe,
qual adaptador usar para upgrade, assim como procedimentos necessários etc

esse repositorio vai ser montado primeiramente como um "mural de recortes" ou rascunho
em seguida vou começar a organizar as informações para facilitar o entendimento.
a prioridade inicial é coletar o maximo de informações o possivel e 'joga-las' aqui
sem me preocupar com infitos commits ou formatação, depois que todas as informações importantes estiverem aqui, vem a foramatação/organização e possivel tradução pro inglês

farei o maximo possivel para dar créditos, postar fontes e referencias
caso haja alguma referencia ausente/errada por favor entre em contato e eu corrijo o quanto antes,
não tenho a intenção de ganhar créditos por trabalho alheio.


## Obter numero de série de Discos

### SATA

```system_profiler SPSerialATADataType -detailLevel medium | awk '/Serial/ {print $NF}'```

### SATA (alternativo)

```ioreg -rd1 -w0 -c AppleAHCIDiskDriver | grep Serial```

### NVMe

```ioreg -rd1 -w0 -c IONVMeBlockStorageDevice | grep "Device Characteristics"```

### outros dispositivos
Internal drives: IOAHCIBlockStorageDevice string property "Serial Number" inside "Device Characteristics" e.g.: (WD-WCAV5D1345345)

USB drives : IOUSBDevice string property "USB Serial Number" e.g.: (5743415654564561373734)

FireWire drives : IOReducedBlockServices number property "GUID" inside "Protocol Characteristics" e.g.: (407345709348650)

[fonte](https://stackoverflow.com/questions/2019244/how-to-get-serial-number-from-mac-hard-disks)

### Número de série do Mac

```ioreg -l | grep IOPlatformSerialNumber```

# LINKS
alguns links são para referenciar imagens outros com informações imporantes

[EveryMac identificador de modelo](https://everymac.com/ultimate-mac-lookup/)

[Mac SSD adapters - hopefully comprehensive view](https://forums.macrumors.com/threads/mac-ssd-adapters-hopefully-comprehensive-view.2328282/)

[possivel fonte para imagens de referencia,loja1](https://www.soarland.com/Macbook_SSD_Adapter-catalog-62.html)

[possivel fonte para imagens de referencia,loja2](https://www.microsatacables.com/drive-adapters-and-drive-converters/apple-ssd-adapter)

[NVMe SSD Upgrade Guide for an Early 2015 MacBook Pro](https://grh.am/2018/nvme-ssd-upgrade-guide-for-an-early-2015-macbook-pro/)

[Upgrading 2013-2015 Macbook Pro SSD to M.2 NVMe](https://forums.macrumors.com/threads/upgrading-2013-2015-macbook-pro-ssd-to-m-2-nvme.2034976/)

[The Ultimate Guide to Apple’s Proprietary SSDs](https://beetstech.com/blog/apple-proprietary-ssd-ultimate-guide-to-specs-and-upgrades)

[PCIe SSDs - NVMe & AHCI](https://forums.macrumors.com/threads/pcie-ssds-nvme-ahci.2146725/)

[SSD Apple, lista de adaptadores e conectores](https://logi.wiki/index.php/Apple_SSD_connectors_and_adapters_list)

[Planilha com todos os SSDs compativeis](https://docs.google.com/spreadsheets/d/1B27_j9NDPU3cNlj2HKcrfpJKHkOf-Oi1DbuuQva2gT4/edit?gid=0#gid=0)
