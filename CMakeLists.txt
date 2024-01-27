cmake_minimum_required(VERSION 3.0.0...3.24 FATAL_ERROR)
project(webgpu VERSION 1.0.0)
include(FetchContent)

message("WebGPU FETCHCONTENT_BASE_DIR=${FETCHCONTENT_BASE_DIR}")

include(FetchContent)

FetchContent_Declare(
	dawn
	#GIT_REPOSITORY https://dawn.googlesource.com/dawn
	#GIT_TAG        chromium/6108
	#GIT_SHALLOW ON

	# Manual download mode, even shallower than GIT_SHALLOW ON
	DOWNLOAD_COMMAND
		cd ${FETCHCONTENT_BASE_DIR}/dawn-src &&
		git init &&
		git fetch --depth=1 https://dawn.googlesource.com/dawn chromium/6108 &&
		git reset --hard FETCH_HEAD
)

FetchContent_MakeAvailable(dawn)
