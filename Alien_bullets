import sys
import pygame
from pygame.sprite import Group
from settings import Settings
import game_functions as gf
from ship import Ship
from button import Button
from scoreboard import Scoreboard
from game_stats import GameStats
from alien import Alien
def run_game():
# 初始化游戏并创建一个屏幕对象
    pygame.init()
    ai_settings = Settings()
    screen = pygame.display.set_mode((ai_settings.screen_width, ai_settings.screen_height))
    pygame.display.set_caption("Alien Invasion")
    play_button = Button(ai_settings, screen, "Play")
    # 创建一艘飞船
    ship = Ship(ai_settings, screen)
    # 创建一组外星人
    aliens = Group()
    # 创建一个用于存储子弹的编组
    bullets = Group()
    # 创建外星人群
    gf.create_fleet(ai_settings, screen, ship, aliens)
    # 创建一个用于存储游戏统计信息的实例
    stats = GameStats(ai_settings)
    # 创建记分牌
    sb = Scoreboard(ai_settings, screen, stats)
    # 开始游戏的主循环
    while True:
        # 监视键盘和鼠标事件
        gf.check_events(ai_settings, screen, stats, sb, play_button, ship,
                        aliens, bullets)
        if stats.game_active:
            # 飞船移动
            ship.update()

            # 删除多余子弹
            gf.update_bullets(ai_settings, screen, stats, sb, ship, aliens, bullets)

            # 外星人移动
            gf.update_aliens(ai_settings, stats, sb, screen, ship, aliens, bullets)

        # 改变屏幕颜色
        gf.update_screen(ai_settings, screen, stats, sb, ship, aliens, bullets, play_button)

run_game()

