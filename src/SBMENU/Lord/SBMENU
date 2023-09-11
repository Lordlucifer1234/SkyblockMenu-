<?php

declare(strict_types=1);

namespace SBMENU\Lord;

use jojoe77777\FormAPI\SimpleForm;
use pocketmine\event\Listener;
use pocketmine\event\player\PlayerInteractEvent;
use pocketmine\event\player\PlayerJoinEvent;
use pocketmine\item\VanillaItems;
use pocketmine\player\Player;
use pocketmine\plugin\PluginBase;

final class SBMENU extends PluginBase implements Listener {

	private const SKYBLOCK_MENU_TAG = "skyblock_menu";

	protected function onEnable(): void {
		$this->getServer()->getPluginManager()->registerEvents($this, $this);
	}

	public function onPlayerJoin(PlayerJoinEvent $event): void {
		$this->giveSkyblockMenu($event->getPlayer());
	}

	public function onPlayerInteract(PlayerInteractEvent $event): void {
		$item = $event->getItem();

		if ($item->getNamedTag()->getTag(self::SKYBLOCK_MENU_TAG)) {
			$this->openSkyblockMenu($event->getPlayer());
		}
	}

	private function openSkyblockMenu(Player $player): void {
		$form = new SimpleForm(function(Player $player, ?int $data = null): void {
			if ($data === null) {
				return;
			}
			$commandName = $this->getCommandName($data);

			if ($commandName !== null) {
				$this->getServer()->dispatchCommand($player, $commandName);
			}
		});

		$form->setTitle("§l§6SKYBLOCK MENU");
		$form->setContent("§dPlease Select The Next Menu:", 0,);
		$form->addButton("§l§eSKYBLOCK\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/skyblock");
		$form->addButton("§l§eRECIPE BOOK\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/recipes");
		$form->addButton("§l§eSKILLS\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/armor");
		$form->addButton("§l§eSHOP\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/shop");
		$form->addButton("§l§eQUESTS\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/quest");
		$form->addButton("§l§eENCHANTMENT SHOP\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/network_hub");
		$form->addButton("§l§eENDER CHEST\n§l§9»» §l§3TAP TO OPEN", 0, "textures/blocks/ender_chest_front");
		$form->addButton("§l§ePOTIONS SHOP\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/icon_potion");
		$form->addButton("§l§ePETS\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/promo_wolf");
		$form->addButton("§l§eWORK BENCH\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/crafting");
		$form->addButton("§l§eAUCTION HOUSE\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/job");
		$form->addButton("§l§eBANK\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/banker");
		$form->addButton("§l§eBLACKSMITH\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/mining");
		$form->addButton("§l§eBAZAAR\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/bazaar");
		$form->addButton("§l§eTRAVEL ISLAND\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/earth");
		$form->addButton("§l§eFAST TRAVEL\n§l§9»» §l§3TAP TO OPEN", 0, "textures/ui/travel");

		$player->sendForm($form);
	}

	private function getCommandName(int $index): ?string {
		$commands = [
			"skyblock",
			"recipes",
			"skills",
			"shop",
			"quests",
			"ceshop",
			"ec",
			"shop Potions",
			"pets",
			"invcraft",
			"ah",
			"bank",
			"blacksmith",
			"bazaar",
			"sbui",
			"ft"
		];

		return $commands[$index] ?? null;
	}

	private function giveSkyblockMenu(Player $player): void {
		$item = VanillaItems::NETHER_STAR()->setCustomName("§r§aSkyblock Menu §7( Right Click )§r");
        $item->setLore(["§r§7View All Of Your Skyblock Progress Including Your Skills,\n§7Collections, Recipes And More!\n\n§r§eClick To Open!"]);

		$item->getNamedTag()->setByte(self::SKYBLOCK_MENU_TAG, 1);

		$player->getInventory()->setItem(8, $item);
	}
}
