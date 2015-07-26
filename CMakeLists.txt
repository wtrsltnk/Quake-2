cmake_minimum_required(VERSION 2.8)
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/")

project(quake2)

set(SRC_QUAKE2
	win32/cd_win.c
	client/cl_cin.c
	client/cl_ents.c
	client/cl_fx.c
	client/cl_input.c
	client/cl_inv.c
	client/cl_main.c
	client/cl_newfx.c
	client/cl_parse.c
	client/cl_pred.c
	client/cl_scrn.c
	client/cl_tent.c
	client/cl_view.c
	qcommon/cmd.c
	qcommon/cmodel.c
	qcommon/common.c
	win32/conproc.c
	client/console.c
	qcommon/crc.c
	qcommon/cvar.c
	qcommon/files.c
	win32/in_win.c
	client/keys.c
	game/m_flash.c
	qcommon/md4.c
	client/menu.c
	qcommon/net_chan.c
	win32/net_wins.c
	qcommon/pmove.c
	game/q_shared.c
	win32/q_shwin.c
	client/qmenu.c
	client/snd_dma.c
	client/snd_mem.c
	client/snd_mix.c
	win32/snd_win.c
	server/sv_ccmds.c
	server/sv_ents.c
	server/sv_game.c
	server/sv_init.c
	server/sv_main.c
	server/sv_send.c
	server/sv_user.c
	server/sv_world.c
	win32/sys_win.c
	win32/vid_dll.c
	win32/vid_menu.c
	client/x86.c
	client/anorms.h
#	qcommon/bspfile.h
	client/cdaudio.h
	client/client.h
	win32/conproc.h
	client/console.h
	game/game.h
	client/input.h
	client/keys.h
	game/q_shared.h
	qcommon/qcommon.h
	qcommon/qfiles.h
	client/qmenu.h
	client/ref.h
	client/screen.h
	server/server.h
	client/snd_loc.h
	client/sound.h
	client/vid.h
	win32/winquake.h
	win32/q2.ico
#	win32/q2.rc
)

add_executable(quake2 WIN32 ${SRC_QUAKE2})

target_link_libraries(quake2 winmm wsock32)

project(gamex86)

set(SRC_GAME
	game/g_ai.c
	game/g_chase.c
	game/g_cmds.c
	game/g_combat.c
	game/g_func.c
	game/g_items.c
	game/g_main.c
	game/g_misc.c
	game/g_monster.c
	game/g_phys.c
	game/g_save.c
	game/g_spawn.c
	game/g_svcmds.c
	game/g_target.c
	game/g_trigger.c
	game/g_turret.c
	game/g_utils.c
	game/g_weapon.c
	game/m_actor.c
	game/m_berserk.c
	game/m_boss2.c
	game/m_boss3.c
	game/m_boss31.c
	game/m_boss32.c
	game/m_brain.c
	game/m_chick.c
	game/m_flash.c
	game/m_flipper.c
	game/m_float.c
	game/m_flyer.c
	game/m_gladiator.c
	game/m_gunner.c
	game/m_hover.c
	game/m_infantry.c
	game/m_insane.c
	game/m_medic.c
	game/m_move.c
	game/m_mutant.c
	game/m_parasite.c
	game/m_soldier.c
	game/m_supertank.c
	game/m_tank.c
	game/p_client.c
	game/p_hud.c
	game/p_trail.c
	game/p_view.c
	game/p_weapon.c
	game/q_shared.c
	game/g_local.h
	game/game.h
	game/m_actor.h
	game/m_berserk.h
	game/m_boss2.h
	game/m_boss31.h
	game/m_boss32.h
	game/m_brain.h
	game/m_chick.h
	game/m_flipper.h
	game/m_float.h
	game/m_flyer.h
	game/m_gladiator.h
	game/m_gunner.h
	game/m_hover.h
	game/m_infantry.h
	game/m_insane.h
	game/m_medic.h
	game/m_mutant.h
	game/m_parasite.h
	game/m_player.h
	game/m_soldier.h
	game/m_supertank.h
	game/m_tank.h
	game/q_shared.h
	game/game.def
)

add_library(gamex86 SHARED ${SRC_GAME})

ADD_CUSTOM_COMMAND(TARGET gamex86 POST_BUILD
	COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_BINARY_DIR}/gamex86.dll ${CMAKE_SOURCE_DIR}/baseq2/gamex86.dll
)

project(ref_gl)

set(SRC_REFGL
	ref_gl/gl_draw.c
	ref_gl/gl_image.c
	ref_gl/gl_light.c
	ref_gl/gl_mesh.c
	ref_gl/gl_model.c
	ref_gl/gl_rmain.c
	ref_gl/gl_rmisc.c
	ref_gl/gl_rsurf.c
	ref_gl/gl_warp.c
	win32/glw_imp.c
	game/q_shared.c
	win32/q_shwin.c
	win32/qgl_win.c
	ref_gl/anorms.h
	ref_gl/anormtab.h
	ref_gl/gl_local.h
	ref_gl/gl_model.h
	win32/glw_win.h
	game/q_shared.h
	qcommon/qcommon.h
	qcommon/qfiles.h
	ref_gl/qgl.h
	client/qmenu.h
	client/ref.h
	ref_gl/#ref_gl.h
	ref_gl/warpsin.h
	win32/winquake.h
	ref_gl/ref_gl.def
)

add_library(ref_gl SHARED ${SRC_REFGL})

target_link_libraries(ref_gl winmm)
