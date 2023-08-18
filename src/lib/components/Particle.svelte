<script lang="ts" context="module">
	const geometry = new BoxGeometry(1, 1, 1);
	const material = new MeshStandardMaterial();
</script>

<script lang="ts">
	import { T } from '@threlte/core';
	import { PositionalAudio } from '@threlte/extras';
	import { Collider, RigidBody, type ContactEvent } from '@threlte/rapier';
	import { writable } from 'svelte/store';
	import type { Euler, Vector3 } from 'three';
	import { BoxGeometry, MeshStandardMaterial } from 'three';
	import { clamp } from 'three/src/math/MathUtils';
	export let position: Vector3 | undefined = undefined;
	export let rotation: Euler | undefined = undefined;

	$: rotationCasted = rotation?.toArray() as [x: number, y: number, z: number];
</script>

<T.Group position={position?.toArray()} rotation={rotationCasted}>
	<RigidBody type={'dynamic'}>
		<Collider
			contactForceEventThreshold={30}
			restitution={0.4}
			shape={'cuboid'}
			args={[0.5, 0.5, 0.5]}
		/>
		<T.Mesh castShadow receiveShadow {geometry} {material} />
	</RigidBody>
</T.Group>
